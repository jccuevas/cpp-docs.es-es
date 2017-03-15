---
title: "_open_osfhandle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_open_osfhandle"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_open_osfhandle"
  - "open_osfhandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "open_osfhandle (función)"
  - "identificadores de archivo [C++], asociar"
  - "_open_osfhandle (función)"
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _open_osfhandle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asocia descriptor de archivo del tiempo de ejecución de C. un identificador de archivo del sistema operativo de existente.  
  
## Sintaxis  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### Parámetros  
 `osfhandle`  
 Identificador de archivo del sistema operativo.  
  
 `flags`  
 Tipos de operaciones permitidas.  
  
## Valor devuelto  
 Si es correcto, `_open_osfhandle` devuelve descriptor de archivo del tiempo de ejecución de C.  De lo contrario, devuelve – 1.  
  
## Comentarios  
 La función de `_open_osfhandle` asigna descriptor de archivo del tiempo de ejecución de C. y lo asocia al identificador de archivo del sistema operativo especificado por `osfhandle`.  El argumento de `flags` es una expresión de tipo entero formada de uno o más de las constantes de manifiesto definidas en Fcntl.h.  Cuando dos o más constantes de manifiesto se utilizan para formar el argumento de `flags` , las constantes se combinan con bit a bit\- OR el operador \(  **&#124;** \).  
  
 Fcntl.h define las constantes de manifiesto siguientes.  
  
 **\_O\_APPEND**  
 Posiciones un puntero de archivo al final del archivo antes de cada operación de escritura.  
  
 **\_O\_RDONLY**  
 Abra el archivo para leer solo.  
  
 **\_O\_TEXT**  
 Abra el archivo en modo de texto \(traducido\).  
  
 **\_O\_WTEXT**  
 Abra el archivo en el modo de Unicode \(UTF\-16 traducido\).  
  
 Para cerrar un archivo abierto con `_open_osfhandle`, llama a `_close`.  El identificador subyacente también es cerrado por una llamada a `_close`, por lo que no es necesario llamar a la función `CloseHandle` Win32 en el identificador original.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_open_osfhandle`|\<io.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)