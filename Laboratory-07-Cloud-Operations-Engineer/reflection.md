# 🚀 Mission Reflection

### *Laboratory 07 – Cloud Operations Engineer*

---

A Cloud Operations Engineer must look beyond the application and check the health of the host server. Containers share the host's CPU, memory, and disk, so even when every container runs perfectly, a full disk or low memory on the host can crash all of them at once. In this lab, checking the baseline with `free -h`, `df -h`, and `top` showed me how much room the server had before the traffic surge. Finding problems early protects the users.

Logs are the next layer of protection. If a user complains that they cannot log in, I would run `docker logs` to see the requests and errors recorded by the application. Codes such as 401, 403, or 500 would show me when the failure happened and what caused it, whether it was wrong credentials, a missing page, or an application crash. In this lab, the 404 line for the hidden-admin-page showed me exactly how a failed request appears.

Logs and metrics are different, but they work together. Logs record individual events, so they explain what happened and why. Metrics, such as the CPU and memory shown by `docker stats`, are numbers measured over time, so they show how healthy the system is right now. Logs help me fix specific errors, while metrics help me plan for more users.

Large companies cannot check thousands of containers by hand. They use **Prometheus** to collect metrics automatically and **Grafana** to display them in clear dashboards. They also set alerts that warn engineers when CPU, memory, or errors become too high, and they store logs in one central place.

Overall, this lab improved my Linux troubleshooting skills. I learned to check the host first, then the application, and to read the output carefully instead of guessing. I also saw that an idle Nginx container uses very little memory. I now feel more confident using the terminal and explaining what the results mean.
