See description

```
if ($env:github_token)
{
    $token = $env:github_token
}
else {
    Write-Host "You must set the 'github_token' env variable!" -ForegroundColor Red
    Exit
}

$apiBase = "https://api.github.com/"
$api2 = $apiBase + "repos/equinor/legacytester"
$body = '{"visibility": "internal"}'

Invoke-RestMethod -Method Patch -Uri $api2 -Body $body -Headers @{Authorization="Token $token"; Accept="application/vnd.github.nebula-preview+json"}
```

Shuffle the $body and put it in a cronjob for some real confusion for your team members.
