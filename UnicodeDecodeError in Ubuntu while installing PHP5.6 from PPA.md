Issue `UnicodeDecodeError in Ubuntu while installing PHP5.6 from PPA.md` on ubuntu 14.04

```
root@xxx:~# apt-add-repository ppa:ondrej/php5-5.6 -y

gpg: keyring `/tmp/tmp9jdzm9kw/secring.gpg' created
gpg: keyring `/tmp/tmp9jdzm9kw/pubring.gpg' created
gpg: requesting key E5267A6C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp9jdzm9kw/trustdb.gpg: trustdb created
gpg: key E5267A6C: public key "Launchpad PPA for Ond\xc5\x99ej Sur�" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python3.4/threading.py", line 920, in _bootstrap_inner
    self.run()
  File "/usr/lib/python3.4/threading.py", line 868, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 687, in addkey_func
    func(**kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 370, in add_key
    return apsk.add_ppa_signing_key()
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 261, in add_ppa_signing_key
    tmp_export_keyring, signing_key_fingerprint, tmp_keyring_dir):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 210, in _verify_fingerprint
    got_fingerprints = self._get_fingerprints(keyring, keyring_dir)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 202, in _get_fingerprints
    output = subprocess.check_output(cmd, universal_newlines=True)
  File "/usr/lib/python3.4/subprocess.py", line 605, in check_output
    output, unused_err = process.communicate(inputdata, timeout=timeout)
  File "/usr/lib/python3.4/subprocess.py", line 936, in communicate
    stdout = _eintr_retry_call(self.stdout.read)
  File "/usr/lib/python3.4/subprocess.py", line 487, in _eintr_retry_call
    return func(*args)
  File "/usr/lib/python3.4/encodings/ascii.py", line 26, in decode
    return codecs.ascii_decode(input, self.errors)[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc5 in position 92: ordinal not in range(128)
```



The proper way is to enable UTF-8 support in your terminal.

First check your locales:

`locale -a`

Then, install an UTF-8 locale, for en_US, the example as follows:

`locale-gen en_US.UTF-8`

Then you need to export it:

`export LANG=en_US.UTF-8`

Then the add-apt-repository command will work okay.

If this still doesn't still work, try using this line:

`LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php`
