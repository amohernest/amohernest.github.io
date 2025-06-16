---
title: "2D Convection-Diffusion Solver with Finite Difference Method"
date: 2023-11-15T14:30:00+01:00
categories:
  - CFD
  - Numerical Methods
tags:
  - MATLAB
  - Finite Difference
  - Upwind Scheme
  - Implicit Discretization
---

## Solving Convection-Dominated Transport Problems

This MATLAB implementation solves the 2D convection-diffusion equation using **implicit time discretization** and **finite difference method**. The code models scalar transport (e.g., temperature or concentration) in a fluid flow field with configurable boundary conditions.

[**View Full Code on GitHub**](https://github.com/yourusername/CFD-solver) <!-- REPLACE WITH YOUR ACTUAL LINK -->

### Physical Setup
- **Domain**: 1m × 1m square
- **Flow**: Uniform 45° velocity field (u = 0.01 m/s)
- **Boundary Conditions**:
  - Left wall: Fixed temperature (T=1)
  - Bottom wall: Fixed temperature (T=0)
  - Top/right walls: Zero-gradient (outflow)
- **Parameters**: Pure convection (α=0), Δt=2s, t_end=200s

## Simulation Results



## Key Numerical Features
```matlab
%% Core Algorithm Structure
while t < t_end
    t = t + dt;
    
    % Assemble matrix: Time + Convection - Diffusion
    Ab = ddt(T,dt) + div(T,ux,uy,dx,dy) - laplacian(T,alpha,dx,dy);
    
    % Apply boundary conditions
    Ab = apply_boundaries(Ab,T);
    
    % Solve linear system
    T = solve(Ab,T);
    
    % Visualize results
    plot2D(x,y,t,T);
end
