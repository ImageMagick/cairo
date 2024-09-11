cairoscript_interpreter_sources = [
  'cairo-script-file.c',
  'cairo-script-hash.c',
  'cairo-script-interpreter.c',
  'cairo-script-objects.c',
  'cairo-script-operators.c',
  'cairo-script-scanner.c',
  'cairo-script-stack.c',
]

cairoscript_interpreter_headers = [
  'cairo-script-interpreter.h',
]

csi_replay_sources = [
  'csi-replay.c',
]

csi_exec_sources = [
  'csi-exec.c',
]

csi_trace_sources = [
  'csi-trace.c',
]

libcairoscript = library('cairo-script-interpreter',
  cairoscript_interpreter_sources,
  include_directories: [incbase],
  dependencies: deps + [libcairo_dep, lzo_dep],
  soversion: cairo_version_sonum,
  version: cairo_libversion,
  c_args: ['-DCAIRO_COMPILATION'],
  link_args: extra_link_args,
  install: true,
)

libcairoscript_dep = declare_dependency(link_with: libcairoscript,
  include_directories: include_directories('.'),
  dependencies: libcairo_dep)

pkgmod.generate(libcairoscript,
  libraries: [libcairo],
  description: 'script surface backend for cairo graphics library',
  subdirs: [meson.project_name()],
)

meson.override_dependency('cairo-script-interpreter', libcairoscript_dep)