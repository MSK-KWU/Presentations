---
marp: true
theme: default
pagiinate: false
class: lead
math: katexs
style: |
    section{
    text-align : left;
    font-family : "Times new Roman"
    }

    h1 {
        font-size: 40px;
        text-align: center;
        font-family: "Times new Roman";
    }

    h2 {
        font-size: 20px;
        text-align: center;
        font-family: "Times new Roman";
        margin: 0;
    }

    h3 {
        font-size: 15px;
        text-align: center;
        font-family: "Times new Roman";
        margin: 0;
    }

    h4 {
        font-size: 40px;
        text-align: left;
        position : absolute;
        top : 30px;
        left : 30px;

        font-family: "Times new Roman";
        margin: 0;
    }
    
    .math-block{
        font-size: 30px;
        text-align: center;
        margin: 0;
    }

    .note {
    font-size: 14px;
    color: gray;
    }


---  
# Speedy-Splat: Fast 3D Gaussian Splatting with Sparse Pixels and Sparse Primitives

### Alex Hanson, Allen Tu, Geng Lin, Vasu Singla, Matthias Zwicker, Tom Goldstein
### University of Maryland, College Park
##
### 2024 arXiv

#

## CVRL
###
## Minsu Kim

---
#### Introduction

![Comparison between 3DGS with Speedy Splat](Speedy_Splat_01.png)
- Does Gaussain Splatting is really "Efficient"?
- So, this paper propose two key contributions: Rendering pipeline optimization, efficient pruning algorithm. 

---

#### Background

- Attributes of 3D gaussians
$$
\mathcal{G} = \{ \mathcal{G}_i = \{ \mu_i, s_i, r_i, h_i, \sigma_i \} \}_{i=1}^N
$$

- Loss term
$$
L(\mathcal{G} \mid \phi, I_{gt}) = \| I_{\mathcal{G}}(\phi) - I_{gt} \|_1 + L_{\text{D-SSIM}}(I_{\mathcal{G}}(\phi), I_{gt})
$$



- test
$$
\rho_M(d^2) =
\begin{cases} 
  \frac{\Gamma - d^2}{T_M}, & \text{if } d^2 < T_M \\
  0, & \text{if } d^2 \geq T_M
\end{cases}
$$

<div class="note">
  - \( \rho_M(d^2) \): Symmetric transfer error.  
  - \( T_M \): Model threshold (e.g., \( T_H, T_F \)).  
  - \( \Gamma \): Parameter for threshold adjustment.
</div>
---
