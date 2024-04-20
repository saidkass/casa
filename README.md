i need assistance to compelete my thesis using Matlab Casadi 
ATTITUDE ANGLE PROTECTION
By using Non-Linear Dynamic Equations 
Pitch Dynamics with Disturbance:
θ_(k+1)=θ_k+□(Δt/Iy) [(I_z-I_x )+qr+L_k ]  +∆θ_(disturbance,k)
Roll Dynamics with Disturbance
α_(k+1)=α_k+□(Δt/Ix) [(I_y-I_z )+pr+M_k ]+∆α_(disturbance,k)
Control Input Dynamics:
Elevator Deflection Dynamics with Disturbance
δ_(elevator,k+i+1)=δ_(elevator,k+i)+∆t/T_e  (δ_(elevator,ref,k+i)-δ_(elevator,k+i) )+
∆δ_(elevator,distubance,k+i)
Aileron Deflection Dynamics with Disturbance
δ_(aileron,k+i+1)=δ_(aileron,k+i)+∆t/T_(δ_aileron )  (δ_(aileron,ref,k+i)-δ_(aileron,k+i) )+
∆δ_(aileron,distubance,k+i)
Protection Mechanism:
Pitch Angle Protection
	
θ_(protected,k+i)=min⁡(θ_max,max⁡(θ_min,θ_(k+i) ) )
Roll Angle Protection
α_(protected,k+i)=min⁡(α_max,max⁡(α_min,α_(k+i) ) )
MPC Cost Function 
Minimize:J=∑_(i=1)^N▒‖[█(θ_(k+i)-θ_(protected,k+i)@α_(k+i)-α_(protected,k+i)@δ_(elevator,k+i)-δ_(elevator,ref,k+i)@δ_(aileron,k+i)-δ_(aileron,ref,k+i) )]‖_Q^2 +‖[δ ̇_(elevator,k+i)¦δ ̇_(aileron,k+i) ]‖_R^2
State Constraints
	Pitch angle constraints: θ_min≤ θ_(k+i)≤θ_max
	Roll angle constraints: α_min≤α_(k+i)≤α_max
Control Input Constraints
	Elevator Deflection Constraints    δ_(elevator,min)≤δ_(elevator,k+i)≤δ_(elevator,max) 
	Aileron Deflection Constraints  δ_(aileron,min)≤δ_(aileron,k+i)≤δ_(aeleron,max) 
Control Input Rate Constraints:
Elevator Deflection Rate Constraints       δ_(elevator,min rate)≤(δ_(elevator,k+i)-δ_(elavator,k+i-1))/∆t≤δ_(elevator,max rate)
Aileron Deflection Rate Constraints:        δ_(aileron,min rate)≤(δ_(aileron,k+i)-δ_(aileron,k+i-1))/∆t≤δ_(aileron,max rate)
	
Disturbance Constraints:
Disturbance Constraints for Pitch and Roll Dynamics:
|∆θ_(disturbance,k+i) |≤ max allowable disturbance for pitch
|∆α_(disturbance,k+i) |≤  max allowable disturbance for roll
Disturbance Constraints for Control Inputs:
|Δδ_(elevator,disturbance,k+1) |≤ max allowable disturbance for elevator
|Δδ_(aileron,disturbance,k+1) |≤ max allowable disturbance for aileron
For real-time or near-real-time solutions, CASADI optimization solvers used solving this problem.
