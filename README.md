`gpustat`
=========

[![pypi](https://img.shields.io/pypi/v/gpustat.svg?maxAge=86400)][pypi_gpustat]
[![Build Status](https://travis-ci.org/wookayin/gpustat.svg?branch=master)](https://travis-ci.org/wookayin/gpustat)
[![license](https://img.shields.io/github/license/wookayin/gpustat.svg?maxAge=86400)](LICENSE)

Just *less* than nvidia-smi?

![Screenshot: gpustat -cp](screenshot.png)

NOTE: This works with NVIDIA Graphics Devices only, no AMD support as of now. Contributions are welcome!

Self-Promotion: A web interface of `gpustat` is available (in alpha)! Check out [gpustat-web][gpustat-web].

[gpustat-web]: https://github.com/wookayin/gpustat-web


Usage
-----

`$ gpustat`

Options:

* `--color`            : Force colored output (even when stdout is not a tty)
* `--no-color`         : Suppress colored output
* `-u`, `--show-user`  : Display username of the process owner
* `-c`, `--show-cmd`   : Display the process name
* `-f`, `--show-full-cmd`   : Display full command and cpu stats of running process
* `-p`, `--show-pid`   : Display PID of the process
* `-F`, `--show-fan`   : Display GPU fan speed
* `-P`, `--show-power` : Display GPU power usage and/or limit (`draw` or `draw,limit`)
* `-a`, `--show-all`   : Display all gpu properties above
* `--watch`, `-i`, `--interval`   : Run in watch mode (equivalent to `watch gpustat`) if given. Denotes interval between updates. ([#41][gh-issue-41])
* `--json`             : JSON Output (Experimental, [#10][gh-issue-10])

### Tips

- To periodically watch, try `gpustat --watch` or `gpustat -i` ([#41][gh-issue-41]).
    - For older versions, one may use `watch --color -n1.0 gpustat --color`.
- Running `nvidia-smi daemon` (root privilege required) will make the query much **faster** and use less CPU ([#54][gh-issue-54]).
- The GPU ID (index) shown by `gpustat` (and `nvidia-smi`) is PCI BUS ID,
  while CUDA differently assigns the fastest GPU with the lowest ID by default.
  Therefore, in order to make CUDA and `gpustat` use **same GPU index**,
  configure the `CUDA_DEVICE_ORDER` environment variable to `PCI_BUS_ID`
  (before setting `CUDA_VISIBLE_DEVICES` for your CUDA program):
  `export CUDA_DEVICE_ORDER=PCI_BUS_ID`.


Quick Installation
------------------

Install from [PyPI][pypi_gpustat]:

```
pip install gpustat
```

If you don't have root privilege, please try to install on user namespace: `pip install --user gpustat`.

To install the latest version (master branch) via pip:

```
pip install git+https://github.com/wookayin/gpustat.git@master
```

Note that starting from v1.0, gpustat will support [only Python 3.4+][gh-issue-66].
For older versions (python 2.7, <3.4), you can continue using gpustat v0.x.


[pypi_gpustat]: https://pypi.python.org/pypi/gpustat
[gh-issue-10]: https://github.com/wookayin/gpustat/issues/10
[gh-issue-41]: https://github.com/wookayin/gpustat/issues/41
[gh-issue-54]: https://github.com/wookayin/gpustat/issues/54
[gh-issue-66]: https://github.com/wookayin/gpustat/issues/66


Changelog
---------

See [CHANGELOG.md](CHANGELOG.md)


License
-------

[MIT License](LICENSE)
