### Modifications to System (Enrollment Dashboard Web Application)

1. **Introducing a Load Balancer**:
   - Place the load balancer in front of the **Enrollment Dashboard Web Application**.
   - Distribute traffic across multiple application instances hosted on different servers.

2. **Adding Multiple Instances**:
   - Deploy additional instances of the **Enrollment Dashboard Web Application**.
   - Instances are identical and can independently serve requests, sharing the load evenly.

3. **Integrating Caching**:
   - Use an in-memory cache to store frequently accessed data like:
     - Course lists.
     - Enrollment status.
     - User session data.
   - Cache reduces the frequency of direct database queries and hence helps when the system grows.
