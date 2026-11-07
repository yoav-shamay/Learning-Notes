Given a vector $(v_1, ..., v_n)$, its polar form is parameters $r, \theta_1, ..., \theta_{n - 1}$ such that:
$$
\begin{matrix}
a_1 = r \sin{\theta_{n - 1}}...\sin{\theta_2}\cos{\theta_1} \\
a_2 = r \sin{\theta_{n - 1}}...\sin{\theta_2}\sin{\theta_1} \\
a_3 = r \sin{\theta_{n - 1}}...\sin{\theta_3}\cos{\theta_2} \\
a_4 = r \sin{\theta_{n - 1}}...\sin{\theta_4}\cos{\theta_3} \\
a_5 = r \sin{\theta_{n - 1}}...\sin{\theta_5}\cos{\theta_4} \\
... \\
a_{k - 1} = r\sin{\theta_{n - 1}}\cos{\theta_{n - 2}} \\
a_k = r\cos{\theta_{n - 1}}
\end{matrix}
$$
$r$ is always unique, and $\theta$ are unique unless $a_1^2 + a_2^2 = 0$.
In the aforementioned case, $\theta_0$ can be any value and the other $\theta$ are uniquely determined. by convention $\theta_0 = 0$.