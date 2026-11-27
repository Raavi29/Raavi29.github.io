# What I sent to OWASP Nettacker, and what was merged

I opened eight pull requests to OWASP Nettacker between 25 March and 4 April 2026. One was merged.

## The merged one: #1487, 15 April 2026

It adds unit tests for the FTP library, which had no test coverage. The tests mock the FTP client, so none of them make a real connection. Its description reports coverage of `ftp.py` rising from 0% to 100%. The pull request adds two test files (`test_ftp.py` and `test_ftps.py`) and a small fix in `ftp.py`: the brute-force method now closes the connection in a `finally` block, so the connection is closed even if a step fails.

## The ones that were not merged

- **Tests for `ssl.py` and `ip.py`:** #1448, #1453 and #1489 added tests for `is_weak_hash_algo` and `get_cert_info`, and #1450 added 61 tests for `core/ip.py` at 83% coverage. All four are closed without merging. #1452, another `is_weak_hash_algo` test, is still open.
- **Fortinet detection modules:** #1502 added a module for CVE-2025-32756 (FortiVoice and FortiMail RCE) and #1490 added one for a FortiWeb CVE (CVE-2025-64446). Both are closed without merging. The feedback on #1502 included testing the module against a real or simulated vulnerable instance, and I closed it.

## Related

I applied to Google Summer of Code 2026 and was not selected. I still contribute.
