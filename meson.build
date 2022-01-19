
project('FreeRTOS', ['c'], default_options : ['c_std=c11', 'warning_level=3'])


allocator = get_option('allocator')
port = get_option('port')

FreeRTOS_inc = include_directories('include/', 'portable/'+port)
FreeRTOS_src = files(
    'croutine.c',
    'event_groups.c',
    'list.c',
    'queue.c',
    'stream_buffer.c',
    'tasks.c',
    'timers.c',
    'portable/'+port+'/port.c',
    'portable/'+port+'/portclib.c',
    'portable/'+port+'/xtensa_init.c',
    'portable/'+port+'/xtemsa_initr.c',
    'portable/'+port+'/xtemsa_overlay_os_hook.c',
    'portable/'+port+'/portasm.S',
    'portable/'+port+'/xtensa_context.S',
    'portable/'+port+'/xtensa_intr_asm.S',
    'portable/'+port+'/xtensa_vectors.S',
    )
    
deps = []
if allocator != ''
    FreeRTOS_src += files('portable/MemMang/'+allocator+'.c')
endif
if port == 'GCC/Posix'
    deps += dependency('threads')
endif

freertos_dep = declare_dependency(dependencies: deps, include_directories: FreeRTOS_inc, sources: FreeRTOS_src)
