# Errors Log

Command failures, exceptions, and unexpected behaviors.

---

## [ERR-20260924-001] faiss-cpu and sentence-transformers installation failed

**Logged**: 2026-09-24T15:20:00Z
**Priority**: high
**Status**: pending
**Area**: infra

### Summary
Attempt to install faiss-cpu and sentence-transformers via pip3 timed out during dependency resolution on ARM architecture.

### Error
```
ERROR: Exception:
Traceback (most recent call last):
  File "/usr/lib/python3.12/site-packages/pip/_vendor/urllib3/response.py", line 438, in _error_catcher:
    yield
  File "/usr/lib/python3.12/site-packages/pip/_vendor/urllib3/response.py", line 561, in read:
    data: bytes = self._fp.read(amt) if not fp_closed else b""
  File "/usr/lib/python3.12/site-packages/pip/_internal/cli/base_command.py", line 105, in _run_wrapper:
    result = self._result = resolver.resolve(...)
  File "/usr/lib/python3.12/site-packages/pip/_vendor/urllib3/response.py", line 443, in raise:
    raise ReadTimeoutError(self._pool, None, "Read timed out.")
pip._vendor.urllib3.exceptions.ReadTimeoutError: HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out.
```

### Context
- Command: pip3 install faiss-cpu sentence-transformers
- Environment: Alpine Linux (aarch64), iSH shell
- Python: 3.12
- Existing packages: numpy 2.1.3, scipy 1.13.1

### Suggested Fix
Try installing faiss-cpu separately first (it has a prebuilt wheel), then install sentence-transformers with timeout increase. If still failing, use Alpine package manager (apk add) or alternative lightweight embedding solutions.

### Metadata
- Reproducible: yes
- Related Files: /var/minis/workspace/weekly_synthesis.py
- See Also: LRN-20260924-004
- Tags: faiss, sentence_transformers, timeout, arm_architecture
