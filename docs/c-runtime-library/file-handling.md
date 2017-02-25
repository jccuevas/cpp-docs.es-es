---
title: "Control de archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.files"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos [C++], controlar"
  - "archivos [C++], manipular"
  - "archivos [C++], abrir"
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# Control de archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Use estas rutinas para crear, eliminar y controlar archivos, y para establecer y comprobar permisos de acceso a archivos.  
  
 Las bibliotecas en tiempo de ejecución de C tienen un límite de 512 para el número de archivos que pueden estar abiertos en un momento dado. Si se intenta abrir un número de descriptores de archivo o de flujos de archivo mayor que el máximo se produce un error del programa. Use [\_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) para cambiar este número.  
  
 Las rutinas siguientes operan sobre los archivos designados por un descriptor de archivos.  
  
### Rutinas de control de archivos \(descriptor de archivos\)  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|------------|---------|-----------------------------------|  
|[\_chsize](../c-runtime-library/reference/chsize.md),[\_chsize\_s](../c-runtime-library/reference/chsize-s.md)|Cambiar el tamaño del archivo|[System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx), [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)|  
|[\_filelength, \_filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Obtener la longitud del archivo|[System::IO::Stream::Length](https://msdn.microsoft.com/en-us/library/system.io.stream.length.aspx), [System::IO::FileStream::Length](https://msdn.microsoft.com/en-us/library/system.io.filestream.length.aspx)|  
|[\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Obtener información de estado del archivo en el descriptor|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_get\_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Devolver el identificador de archivo del sistema operativo asociado al descriptor de archivo del tiempo de ejecución de C existente|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_isatty](../c-runtime-library/reference/isatty.md)|Comprobar el dispositivo de caracteres|[System::IO::Stream::CanWrite](https://msdn.microsoft.com/en-us/library/system.io.filestream.canwrite.aspx), [System::IO::FileStream::CanWrite](https://msdn.microsoft.com/en-us/library/system.io.stream.canwrite.aspx)|  
|[\_locking](../c-runtime-library/reference/locking.md)|Bloquear partes del archivo|[System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)|  
|[\_open\_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Asociar el descriptor de archivo del tiempo de ejecución de C al identificador de archivo del sistema operativo existente|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[\_setmode](../c-runtime-library/reference/setmode.md)|Establecer el modo de traducción de archivo|[System::IO::BinaryReader Class](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.aspx), [System::IO::TextReader Class](https://msdn.microsoft.com/en-us/library/system.io.textreader.aspx)|  
  
 Las rutinas siguientes operan sobre archivos especificados por una ruta de acceso o nombre de archivo.  
  
### Rutinas de control de archivos \(ruta de acceso o nombre de archivo\)  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|------------|---------|-----------------------------------|  
|[\_access, \_waccess](../c-runtime-library/reference/access-waccess.md), [\_access\_s, \_waccess\_s](../c-runtime-library/reference/access-s-waccess-s.md)|Comprobar la configuración de los permisos de archivo|[Enumeración System::IO::FileAccess](https://msdn.microsoft.com/en-us/library/4z36sx0f.aspx)|  
|[\_chmod, \_wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Cambiar la configuración de los permisos de archivo|[System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx), [System::Security::Permissions::FileIOPermission](https://msdn.microsoft.com/en-us/library/system.security.permissions.fileiopermission.aspx)|  
|[\_fullpath, \_wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Expandir una ruta de acceso relativa al nombre de ruta de acceso absoluta|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[\_makepath, \_wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [\_makepath\_s, \_wmakepath\_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Combinar componentes de ruta de acceso para formar una ruta de acceso única y completa|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[\_mktemp, \_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md), [\_mktemp\_s, \_wmktemp\_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Crear nombre de archivo único|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[remove, \_wremove](../c-runtime-library/reference/remove-wremove.md)|Eliminar archivo|[System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)|  
|[rename, \_wrename](../c-runtime-library/reference/rename-wrename.md)|Cambiar nombre de archivo|[System::IO::File::Move](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)|  
|[\_splitpath, \_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md), [\_splitpath\_s, \_wsplitpath\_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Analizar los componentes de la ruta de acceso|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_stat, \_stat64, \_stati64, \_wstat, \_wstat64, \_wstati64](../c-runtime-library/reference/stat-functions.md)|Obtener información de estado del archivo sobre el archivo con nombre|[System::IO::File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.getattributes.aspx), [System::IO::File::GetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.getcreationtime.aspx), [System::IO::File::GetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastaccesstime.aspx), [System::IO::File::GetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastwritetime.aspx)|  
|[\_umask](../c-runtime-library/reference/umask.md), [\_umask\_s](../c-runtime-library/reference/umask-s.md)|Establecer la máscara de permisos predeterminada para los nuevos archivos creados por el programa|[System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)|  
|[\_unlink, \_wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Eliminar archivo|[System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)|  
  
 Las rutinas siguientes abren archivos.  
  
### Rutinas de control de archivos \(abrir archivo\)  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|------------|---------|-----------------------------------|  
|[fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen\_s, \_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Abrir un archivo y devolver un puntero al archivo abierto|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx), <xref:System.IO.FileStream.%23ctor%2A>|  
|[\_fsopen, \_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Abrir un flujo con uso compartido de archivos y devolver un puntero al archivo abierto|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx), <xref:System.IO.FileStream.%23ctor%2A>|  
|[\_open, \_wopen](../c-runtime-library/reference/open-wopen.md)|Abrir un archivo y devolver un descriptor de archivo del archivo abierto|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx), <xref:System.IO.FileStream.%23ctor%2A>|  
|[\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md), [\_sopen\_s, \_wsopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Abrir un archivo con el uso compartido de archivos y devolver un descriptor de archivo al archivo abierto||  
|[\_pipe](../c-runtime-library/reference/pipe.md)|Crear una canalización de lectura y escritura.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[freopen, \_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen\_s, \_wfreopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Reasignar un puntero de archivo|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx), <xref:System.IO.FileStream.%23ctor%2A>|  
  
 Las funciones siguientes proporcionan una forma de cambiar la representación del archivo, que puede ser una estructura de `FILE`, un descriptor de archivo o un identificador de archivos de Win32.  
  
||||  
|-|-|-|  
|[\_fdopen, \_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Asociar un flujo a un archivo que se ha abierto previamente para E\/S de bajo nivel y devolver un puntero al flujo abierta|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.filestream.aspx)|  
|[\_fileno](../c-runtime-library/reference/fileno.md)|Obtener el descriptor de archivo asociado a un flujo|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[\_get\_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Devolver el identificador de archivo del sistema operativo asociado al descriptor de archivo del tiempo de ejecución de C existente|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_open\_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Asociar el descriptor de archivo del tiempo de ejecución de C al identificador de archivo del sistema operativo existente|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
  
 Las siguientes funciones de Win32 también abren archivos y canalizaciones:  
  
-   [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)  
  
-   [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)  
  
-   [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx)  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Control de directorio](../c-runtime-library/directory-control.md)   
 [Llamadas del sistema](../c-runtime-library/system-calls.md)