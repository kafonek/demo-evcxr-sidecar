# demo-evcxr-sidecar

Created for the conversation in https://github.com/denoland/deno/pull/20337#issuecomment-1707152309

# Run

To replicate what's going on in the Notebook, [install evcxr](https://github.com/evcxr/evcxr/blob/main/evcxr_jupyter/README.md) then run it with `❯ exec evcxr_jupyter --control_file conn.json`

Install the Python libraries in this repo with `poetry install`.

After that you should be able to test sending kernel info requests and execute requests using the `kernel-sidecar` CLI or by using `kernel-sidecar` in a Notebook.

```
~/evtest is 📦 v0.1.0 via 🐍 v3.10.8 (evtest-py3.10) took 4s
❯ sidecar -f conn.json
2023-09-05T19:12:19.503283Z [info     ] Attempting to connect:
{'control_port': 50005,
 'hb_port': 50004,
 'iopub_port': 50003,
 'ip': '0.0.0.0',
 'kernel_name': 'rust-1.70',
 'key': 'd3bafc903c6e4efc961f0223cd1d9cc1',
 'session': None,
 'shell_port': 50001,
 'signature_scheme': 'hmac-sha256',
 'stdin_port': 50002,
 'transport': 'tcp'} [kernel_sidecar.cli] filename=cli.py func_name=main lineno=72
2023-09-05T19:12:21.210602Z [info     ] {'banner': 'EvCxR 0.14.2 - Evaluation Context for Rust',
 'debugger': None,
 'help_links': [{'text': 'Rust std docs',
                 'url': 'https://doc.rust-lang.org/stable/std/'}],
 'implementation': 'evcxr_jupyter',
 'implementation_version': '0.14.2',
 'language_info': {'codemirror_mode': 'rust',
                   'file_extension': '.rs',
                   'mimetype': 'text/rust',
                   'name': 'Rust',
                   'nbconvert_exporter': None,
                   'pygment_lexer': 'rust',
                   'pygments_lexer': None,
                   'version': ''},
 'protocol_version': '5.3',
 'status': 'ok'} [kernel_sidecar.cli] filename=cli.py func_name=connect lineno=47

~/evtest is 📦 v0.1.0 via 🐍 v3.10.8 (evtest-py3.10) took 2s
❯ sidecar -f conn.json --execute 'println!("Rusty")'
2023-09-05T19:13:06.401621Z [info     ] Attempting to connect:
{'control_port': 50005,
 'hb_port': 50004,
 'iopub_port': 50003,
 'ip': '0.0.0.0',
 'kernel_name': 'rust-1.70',
 'key': 'd3bafc903c6e4efc961f0223cd1d9cc1',
 'session': None,
 'shell_port': 50001,
 'signature_scheme': 'hmac-sha256',
 'stdin_port': 50002,
 'transport': 'tcp'} [kernel_sidecar.cli] filename=cli.py func_name=main lineno=72
2023-09-05T19:13:06.798487Z [info     ] Rusty
                         [kernel_sidecar.cli] filename=cli.py func_name=handle_stream lineno=26
2023-09-05T19:13:06.801017Z [info     ] {'text/plain': '()'}           [kernel_sidecar.cli] filename=cli.py func_name=handle_execute_result lineno=31
```
