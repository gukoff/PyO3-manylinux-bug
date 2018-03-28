# word-count


`word-count` is taken from [PyO3](https://github.com/PyO3/pyo3/tree/2aedbffcd01e05a8b0d1572ab87561db6ec79835/examples/word-count).

`build_wheels.sh` is taken from [setuptools-rust](https://github.com/PyO3/setuptools-rust/blob/605cadb/example/build-wheels.sh).



#### Trying to build on manylinux:
```bash
docker run --rm -v `pwd`:/io quay.io/pypa/manylinux1_x86_64 /io/build_wheels.sh
```



#### Getting the error:

```
+ mkdir /root/rust-installer
+ curl -sL https://static.rust-lang.org/rustup.sh -o /root/rust-installer/rustup.sh
+ sh /root/rust-installer/rustup.sh '--prefix=~/rust' --spec=nightly -y --disable-sudo
rustup: gpg not available. signatures will not be verified
rustup: downloading manifest for 'nightly'
rustup: downloading toolchain for 'nightly'
######################################################################## 100.0%
rustup: installing toolchain for 'nightly'
rustup: extracting installer
install: creating uninstall script at /root/rust/lib/rustlib/uninstall.sh
install: installing component 'rustc'
install: installing component 'cargo'
install: installing component 'rls-preview'
install: installing component 'rustfmt-preview'
install: installing component 'rust-analysis-x86_64-unknown-linux-gnu'
install: installing component 'rust-std-x86_64-unknown-linux-gnu'
install: installing component 'rust-docs'
 
    Rust is ready to roll.
 
+ export PATH=/root/rust/bin:/opt/rh/devtoolset-2/root/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
+ PATH=/root/rust/bin:/opt/rh/devtoolset-2/root/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
+ export LD_LIBRARY_PATH=/opt/rh/devtoolset-2/root/usr/lib64:/opt/rh/devtoolset-2/root/usr/lib:/usr/local/lib64:/usr/local/lib:/root/rust/lib
+ LD_LIBRARY_PATH=/opt/rh/devtoolset-2/root/usr/lib64:/opt/rh/devtoolset-2/root/usr/lib:/usr/local/lib64:/usr/local/lib:/root/rust/lib
+ for PYBIN in '/opt/python/cp{27,35,36}*/bin'
++ /opt/python/cp27-cp27m/bin/python -c 'import sysconfig; print(sysconfig.get_config_var('\''LIBDIR'\''))'
+ export PYTHON_LIB=/opt/_internal/cpython-2.7.14-ucs2/lib
+ PYTHON_LIB=/opt/_internal/cpython-2.7.14-ucs2/lib
+ export LIBRARY_PATH=:/opt/_internal/cpython-2.7.14-ucs2/lib
+ LIBRARY_PATH=:/opt/_internal/cpython-2.7.14-ucs2/lib
+ export LD_LIBRARY_PATH=/opt/rh/devtoolset-2/root/usr/lib64:/opt/rh/devtoolset-2/root/usr/lib:/usr/local/lib64:/usr/local/lib:/root/rust/lib:/opt/_internal/cpython-2.7.14-ucs2/lib
+ LD_LIBRARY_PATH=/opt/rh/devtoolset-2/root/usr/lib64:/opt/rh/devtoolset-2/root/usr/lib:/usr/local/lib64:/usr/local/lib:/root/rust/lib:/opt/_internal/cpython-2.7.14-ucs2/lib
+ /opt/python/cp27-cp27m/bin/pip install -U setuptools setuptools-rust wheel
Collecting setuptools
  Downloading setuptools-39.0.1-py2.py3-none-any.whl (569kB)
Collecting setuptools-rust
  Downloading setuptools-rust-0.9.1.tar.gz
Requirement already up-to-date: wheel in /opt/_internal/cpython-2.7.14-ucs2/lib/python2.7/site-packages
Collecting semantic_version>=2.6.0 (from setuptools-rust)
  Downloading semantic_version-2.6.0.tar.gz
Building wheels for collected packages: setuptools-rust, semantic-version
  Running setup.py bdist_wheel for setuptools-rust: started
  Running setup.py bdist_wheel for setuptools-rust: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/ff/87/7a/0dead6a7aef386e48867db8f7ffd77823a443c35d3fa17715f
  Running setup.py bdist_wheel for semantic-version: started
  Running setup.py bdist_wheel for semantic-version: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/8e/b7/80/adcc81f7455c6fe108fa530c1dfb5ba037091ff7c633013224
Successfully built setuptools-rust semantic-version
Installing collected packages: setuptools, semantic-version, setuptools-rust
  Found existing installation: setuptools 38.4.0
    Uninstalling setuptools-38.4.0:
      Successfully uninstalled setuptools-38.4.0
Successfully installed semantic-version-2.6.0 setuptools-39.0.1 setuptools-rust-0.9.1
You are using pip version 9.0.1, however version 9.0.3 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
+ RUST_BACKTRACE=1
+ /opt/python/cp27-cp27m/bin/pip wheel /io/ -w /io/dist/
Processing /io
Building wheels for collected packages: word-count
  Running setup.py bdist_wheel for word-count: started
  Running setup.py bdist_wheel for word-count: still running...
  Running setup.py bdist_wheel for word-count: still running...
  Running setup.py bdist_wheel for word-count: still running...
  Running setup.py bdist_wheel for word-count: still running...
  Running setup.py bdist_wheel for word-count: finished with status 'error'
  Complete output from command /opt/_internal/cpython-2.7.14-ucs2/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-sHw2jX-build/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" bdist_wheel -d /tmp/tmphUFvZPpip-wheel-:
  running bdist_wheel
  running build
  running build_py
  creating build/lib
  creating build/lib/word_count
  copying word_count/__init__.py -> build/lib/word_count
  running egg_info
  writing word_count.egg-info/PKG-INFO
  writing top-level names to word_count.egg-info/top_level.txt
  writing dependency_links to word_count.egg-info/dependency_links.txt
  reading manifest file 'word_count.egg-info/SOURCES.txt'
  writing manifest file 'word_count.egg-info/SOURCES.txt'
  running build_ext
  running build_rust
  cargo rustc --lib --manifest-path Cargo.toml --features pyo3/extension-module pyo3/python2 --release -- --crate-type cdylib
      Updating registry `https://github.com/rust-lang/crates.io-index`
   Downloading rayon v0.8.2
   Downloading pyo3 v0.2.5
   Downloading rayon-core v1.4.0
   Downloading num_cpus v1.8.0
   Downloading rand v0.4.2
   Downloading lazy_static v1.0.0
   Downloading libc v0.2.40
   Downloading crossbeam-deque v0.2.0
   Downloading crossbeam-utils v0.2.2
   Downloading crossbeam-epoch v0.3.1
   Downloading cfg-if v0.1.2
   Downloading arrayvec v0.4.7
   Downloading nodrop v0.1.12
   Downloading scopeguard v0.3.3
   Downloading memoffset v0.2.1
   Downloading num-traits v0.2.2
   Downloading pyo3cls v0.2.1
   Downloading spin v0.4.7
   Downloading log v0.4.1
   Downloading syn v0.11.11
   Downloading log v0.3.9
   Downloading quote v0.3.15
   Downloading unicode-xid v0.0.4
   Downloading synom v0.11.3
   Downloading version_check v0.1.3
   Downloading regex v0.2.10
   Downloading regex-syntax v0.5.3
   Downloading memchr v2.0.1
   Downloading utf8-ranges v1.0.0
   Downloading aho-corasick v0.6.4
   Downloading thread_local v0.3.5
   Downloading ucd-util v0.1.1
   Downloading unreachable v1.0.0
   Downloading void v1.0.2
     Compiling void v1.0.2
     Compiling libc v0.2.40
     Compiling lazy_static v1.0.0
     Compiling ucd-util v0.1.1
     Compiling regex v0.2.10
     Compiling nodrop v0.1.12
     Compiling cfg-if v0.1.2
     Compiling unicode-xid v0.0.4
     Compiling utf8-ranges v1.0.0
     Compiling memoffset v0.2.1
     Compiling scopeguard v0.3.3
     Compiling quote v0.3.15
     Compiling version_check v0.1.3
     Compiling rayon-core v1.4.0
     Compiling spin v0.4.7
     Compiling num-traits v0.2.2
     Compiling unreachable v1.0.0
     Compiling regex-syntax v0.5.3
     Compiling memchr v2.0.1
     Compiling rand v0.4.2
     Compiling num_cpus v1.8.0
     Compiling arrayvec v0.4.7
     Compiling crossbeam-utils v0.2.2
     Compiling log v0.4.1
     Compiling synom v0.11.3
     Compiling thread_local v0.3.5
     Compiling aho-corasick v0.6.4
     Compiling crossbeam-epoch v0.3.1
     Compiling log v0.3.9
     Compiling syn v0.11.11
     Compiling crossbeam-deque v0.2.0
     Compiling pyo3 v0.2.5
     Compiling pyo3cls v0.2.1
     Compiling rayon v0.8.2
  error: failed to run custom build command for `pyo3 v0.2.5`
  process didn't exit successfully: `/tmp/pip-sHw2jX-build/build/temp.linux-x86_64-2.7/word-count/release/build/pyo3-aea46c0f50a8070f/build-script-build` (exit code: 101)
  --- stderr
  thread 'main' panicked at 'called `Result::unwrap()` on an `Err` value: "python script failed with stderr:\n\nTraceback (most recent call last):\n  File \"<string>\", line 1, in ?\nImportError: No module named sysconfig\n"', libcore/result.rs:945:5
  stack backtrace:
     0: std::sys::unix::backtrace::tracing::imp::unwind_backtrace
               at libstd/sys/unix/backtrace/tracing/gcc_s.rs:49
     1: std::sys_common::backtrace::print
               at libstd/sys_common/backtrace.rs:71
               at libstd/sys_common/backtrace.rs:59
     2: std::panicking::default_hook::{{closure}}
               at libstd/panicking.rs:207
     3: std::panicking::default_hook
               at libstd/panicking.rs:223
     4: std::panicking::rust_panic_with_hook
               at libstd/panicking.rs:402
     5: std::panicking::begin_panic_fmt
               at libstd/panicking.rs:349
     6: rust_begin_unwind
               at libstd/panicking.rs:325
     7: core::panicking::panic_fmt
               at libcore/panicking.rs:72
     8: core::result::unwrap_failed
     9: build_script_build::main
    10: std::rt::lang_start::{{closure}}
    11: std::panicking::try::do_call
               at libstd/rt.rs:59
               at libstd/panicking.rs:306
    12: __rust_maybe_catch_panic
               at libpanic_unwind/lib.rs:102
    13: std::rt::lang_start_internal
               at libstd/panicking.rs:285
               at libstd/panic.rs:361
               at libstd/rt.rs:58
    14: main
    15: __libc_start_main
    16: <unknown>
 
  warning: build failed, waiting for other jobs to finish...
  error: build failed
  error: cargo failed with code: 101
 
 
  ----------------------------------------
  Failed building wheel for word-count
  Running setup.py clean for word-count
Failed to build word-count
ERROR: Failed to build one or more wheels
You are using pip version 9.0.1, however version 9.0.3 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```
