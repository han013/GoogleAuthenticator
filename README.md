# GoogleAuthenticator
Google身份验证器, Google两步验证，Google Authenticator， 2-factor authentication

```php
<?php
require_once 'Hanhan/GoogleAuthenticator.php';

$google = new GoogleAuthenticator();
$secret = $google->createSecret();
echo "Secret is: ".$secret."\n\n";

$qrCodeUrl = $google->getQRCodeGoogleUrl('Blog', $secret);
echo "Google Charts URL for the QR-Code: ".$qrCodeUrl."\n\n";

$oneCode = $google->getCode($secret);
echo "Checking Code '$oneCode' and Secret '$secret':\n";

$checkResult = $google->verifyCode($secret, $oneCode, 2);    // 2 = 2*30sec clock tolerance
if ($checkResult) {
    echo 'OK';
} else {
    echo 'FAILED';
}
```