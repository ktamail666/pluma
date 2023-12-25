cargs = [
  '-DPLUMA_DATADIR="@0@"'.format(datadir),
]

libdialogs = static_library(
  'dialogs',
  sources : [
	'pluma-preferences-dialog.h',
	'pluma-preferences-dialog.c',
	'pluma-close-confirmation-dialog.c',
	'pluma-close-confirmation-dialog.h',
	'pluma-encodings-dialog.c',
	'pluma-encodings-dialog.h',
	'pluma-search-dialog.h',
	'pluma-search-dialog.c'
  ],
  include_directories : [
    include_directories('..'),
    include_directories('../../', is_system:true),
    ],
  dependencies : term_deps,
  install: false,
  c_args : cargs
)

