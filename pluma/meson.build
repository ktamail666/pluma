cargs = [
  '-DDATADIR="@0@"'.format(datadir),
  '-DLIBDIR="@0@"'.format(libdir),
  '-DPLUMA_LIBDIR="@0@"'.format(libdir),
  '-DPLUMA_DATADIR="@0@/pluma"'.format(datadir),
  '-DPLUMA_LOCALEDIR="@0@/locale"'.format(datadir),
  '-Wno-deprecated-declarations'
]

sources = [
	'pluma-app.c',
	'pluma-app-activatable.c', 
	'pluma-close-button.c',
	'pluma-commands-documents.c',
	'pluma-commands-edit.c',
	'pluma-commands-file.c',
	'pluma-commands-file-print.c',
	'pluma-commands-help.c',
	'pluma-commands-search.c',
	'pluma-commands-view.c',
	'pluma-debug.c',
	'pluma-dirs.c',
	'pluma-document.c', 
	'pluma-document-input-stream.c',
	'pluma-document-loader.c',
	'pluma-document-output-stream.c',
	'pluma-document-saver.c',
	'pluma-documents-panel.c',
	'pluma-encodings.c',
	'pluma-encodings-combo-box.c',
	'pluma-file-chooser-dialog.c',
	'pluma-help.c',
	'pluma-history-entry.c',
	'pluma-io-error-message-area.c',
	'pluma-language-manager.c',
	'pluma-message-bus.c',
	'pluma-message-type.c',
	'pluma-message.c',
	'pluma-notebook.c',
	'pluma-panel.c',
	'pluma-pango.c',
	'pluma-plugins-engine.c',
	'pluma-print-job.c',
	'pluma-print-preview.c',
	'pluma-progress-message-area.c',
	'pluma-session.c',
	'pluma-settings.c',
	'pluma-smart-charset-converter.c',
	'pluma-statusbar.c',
	'pluma-status-combo-box.c',
	'pluma-style-scheme-manager.c',
	'pluma-tab.c', 
	'pluma-tab-label.c',
	'pluma-utils.c', 
	'pluma-view.c', 
	'pluma-view-activatable.c', 
	'pluma-window.c',
	'pluma-window-activatable.c', 
	'plumatextregion.c',
	
	# TODO 
	'pluma-enum-types.c',
	'pluma-metadata-manager.c',
	'bacon-message-connection.c'
]

libpluma = library(
  'pluma',
  sources : [
    'pluma.c',
    sources
  ],
  include_directories : [
    include_directories('..'),
    ],
  dependencies : term_deps,
  link_with : [
    libdialogs,
  ],
  install: false,
  c_args : cargs
)

