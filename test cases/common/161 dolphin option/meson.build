project('dolphin option', 'c')

x264_dep = dependency('x264', options : ['video', 'patented'])
unfound_dep = dependency('notfound', required : false)

exe = executable('encprog', 'encprog.c',
  dependencies : x264_dep)
test('enc test', exe)

subdir('nogo', if_found : x264_dep)
subdir('nogo', if_found : unfound_dep)

gs = custom_target('somec',
  input : 'proggie.c.in',
  output : 'proggie.c',
  command : [exe, '@INPUT@', '@OUTPUT@'],
  )

test('Generated test', executable('proggie', gs))

if not meson.is_cross_build() and find_program('pkg-config', required:false).found()
  subdir('deplookups')
endif

