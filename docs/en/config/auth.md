# Authentication

Corresponds to the `auth` section of the configuration file.

| Field              | Type   | Default  | Description                                                                                     |
|--------------------|--------|----------|----------------------------------------------------------------.................................|
| `jwt_secret`       | string | Generated automatically | Signing key of the login token, randomly generated on first start. **Do not leak or change it casually**; all users have to sign in again after it changes. |
| `token_expires_in` | int    | `7`      | Validity period of the login token (**in days**).                                                |
