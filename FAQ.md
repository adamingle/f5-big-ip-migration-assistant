# F5 BIG-IP Migration Assistant FAQ

A list of questions and answers:

### Q: Is my configuration and platform eligible to use this tool?

If the answer to any of the following questions is **Yes**, then you are *not* eligible:

1. Is your current or target BIG-IP® instance FIPS-enabled?
1. Is your current BIG-IP instance running in Appliance/Common Criteria mode?
1. Is your current BIG-IP instance running a version earlier than 11.1.0?
1. If your target BIG-IP instance is running a 12.x release, is the version earlier than 12.1.3?
1. If your target BIG-IP instance is running a 13.x release, is the version earlier than 13.1.0?

### Q: When I upload a UCS file into Migration Assistant, it says **"Invalid UCS"**.  I know it's valid. Why is it claiming it isn't?

This issue occurs under the following conditions:

1. The UCS file is encrypted at generation time.
1. The UCS file is damaged during download from the source BIG-IP device.

In either case, go back to your source BIG-IP device and generate a new, unencrypted UCS file. Make sure to include the private keys if you want your target BIG-IP device to be fully functional.

[Back to README](README.md)