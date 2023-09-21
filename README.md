# issue 5349
### Summary
- google-services:4.4.0 is incompatible with appdistribution:4.0.0
- 
### Steps to reproduce
- Open app
- Use version `com.google.gms.google-services:4.4.0`
- Clean and rebuild the project
- Use `export GOOGLE_APPLICATION_CREDENTIALS=....` in terminal
- Run `gradle app:assembleDebug app:appDistributionUploadDebug` (error missing app id is encountered)

Since App distribution uses cached Firebase CLI credentials.
### Incorrect scenario
- Use version `com.google.gms.google-services:4.3.15`
- Use `export GOOGLE_APPLICATION_CREDENTIALS=....` in terminal
- Run gradle `app:assembleDebug app:appDistributionUploadDebug` (works)
- Update to version `com.google.gms.google-services:4.4.0`
- Run `gradle app:assembleDebug app:appDistributionUploadDebug` (works, because of the cached credential)
