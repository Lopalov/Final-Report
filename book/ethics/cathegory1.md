+++
# Ethics Category 1: Proccessing Personal Data

A core ethical consideration in our project is the handling of personal data, particularly information obtained from users’ GitHub accounts. During authentication, the application requests a GitHub Personal Access Token (PAT) and retrieves profile details such as the username and user ID. This data is displayed in the interface and enables personalized features and access to GitHub repositories.

## Key Ethical Concerns

*   **Token Sensitivity** - Personal Access Tokens grant access to users’ repositories and account information. Mishandling these tokens could result in unauthorized access or security breaches.
*   **Privacy of User Information** - Even public profile data (e.g., username, avatar) carries privacy implications when displayed or stored without consent. Users should retain control over how their information is used within the editor.
*   **User Consent and Awareness** - Users may not fully understand the implications of using a PAT or what permissions they are granting. Without proper communication, this can lead to uninformed consent.

## Risk Mitigation Strategies

*   **Manual Authentication** - Instead of automatic OAuth flows (which are more vulnerable to interception), we require users to manually generate and input their GitHub PAT. This approach ensures that users are aware of what permissions they are granting.
*   **Local Storage Only** - The PAT is stored solely in the browser’s local storage and is never transmitted to any backend server, reducing the risk of leaks or breaches.
*   **Minimal Permissions** - We guide users to create fine-grained tokens with only the minimum required scopes (e.g., access to a single repo), limiting potential damage in case of token exposure.

By keeping all authentication local and clearly communicating the authentication process, we prioritize user privacy and safety.