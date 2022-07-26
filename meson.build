project('amp', 'cpp', 'c', license: 'GPL-3.0-or-later', version: '2.0',
  default_options : ['buildtype=release'])

cc = meson.get_compiler('cpp')
m_dep = cc.find_library('m', required : false)
cxx = meson.get_compiler('cpp')

boost = cxx.has_header('boost/circular_buffer.hpp', required: true)
xcb = dependency('xcb', required: get_option('gui'))
xcb_aux = dependency('xcb-aux', required: xcb.found())
xcb_icccm = dependency('xcb-icccm', required: xcb.found())
cairo = dependency('cairo', required: get_option('gui'))

faust = find_program('faust', required: true)
faustarch = run_command(faust, '-archdir', check: true).stdout().strip()

lv2 = dependency('lv2', required: get_option('lv2'))

if not lv2.found() and not ladspa
  error('must enable either ladspa or lv2')
endif

plugins = {
  'profiler': {
    'gui': false,
    'lv2src': ['profiler.cpp'],
    'libs': ['zita-convolver', 'zita-resampler']
  },
}

add_project_arguments(
          '-DFAUST_META=1',
          '-DFAUST_MIDICC=1',
          '-DFAUST_MTS=1',
          '-DVOICE_CTRLS=1', language: ['c', 'cpp'])

if lv2.found()
  subdir('LV2')
endif
