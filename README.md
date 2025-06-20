# AuthFi API Python Client

A comprehensive Python wrapper for the Authentrend AuthFi WebAuthn/FIDO2 API, providing easy-to-use methods for authentication, registration, and user management.

## Features

- **WebAuthn/FIDO2 Support**: Complete implementation of WebAuthn standards
- **Mobile Authentication**: Support for mobile authenticator apps
- **User Management**: Create, list, suspend, and delete users
- **Credential Management**: Manage authentication keys and credentials
- **QR Code Generation**: Generate QR codes for mobile registration and verification
- **Type Safety**: Full type hints and validation using Pydantic
- **Error Handling**: Comprehensive error codes and messages

## Installation

```bash
pip install authfi-api
```

## Quick Start

```
from authfi import AuthFiApi
from fido2.webauthn import UserVerificationRequirement

# Initialize the API client
api = AuthFiApi(
    api_accesspoint="https://authfi.authentrend.com/your-endpoint",
    api_key="your-api-key"
)

# Begin user registration
response = api.register_begin(
    user_name="user@example.com",
    user_display_name="John Doe"
)

# List registered users
users = api.list_users(page=1, size=20)

# Generate QR code for mobile registration
qr_response = api.generate_registration_qrcode(
    user_name="user@example.com",
    path="/callback"
)
```

## API Methods

### Registration

register_begin() - Begin WebAuthn registration
register_complete() - Complete WebAuthn registration
npk_register_begin() - Begin mobile (non-passkey) registration
npk_register_complete() - Complete mobile registration

### Authentication

login_begin() - Begin WebAuthn login
login_complete() - Complete WebAuthn login
authenticate_begin() - Begin authentication
authenticate_complete() - Complete authentication
npk_authenticate_begin() - Begin mobile authentication
npk_authenticate_complete() - Complete mobile authentication

### User Management

list_users() - List all users
set_user_state() - Activate or suspend users
delete_user() - Delete a user

### Credential Management

list_keys() - List user's credentials
set_key_name() - Set friendly name for credentials
delete_key() - Delete a credential

### Mobile/QR Code

generate_registration_qrcode() - Generate registration QR code
get_registration_status() - Check registration status
get_registered_username() - Get registered username
generate_verification_qrcode() - Generate verification QR code
get_verification_status() - Check verification status

## Configuration

The AuthFiApi class accepts the following parameters:

- api_accesspoint (str): Your AuthFi API endpoint URL
- api_key (str): Your AuthFi API key
- timeout (int): Request timeout in seconds (default: 10)
- authenticator_attachment: Default authenticator attachment preference
- require_resident_key: Default resident key requirement
- user_verification: Default user verification requirement
- attestation: Default attestation conveyance preference

## Error Handling
The package includes comprehensive error handling with descriptive error messages:
