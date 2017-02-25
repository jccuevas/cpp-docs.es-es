---
title: "E/S de bajo nivel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "identificadores de archivos [C++]"
  - "identificadores de archivos [C++], E/S (funciones)"
  - "E/S [CRT], funciones"
  - "E/S [CRT], bajo nivel"
  - "rutinas de E/S de bajo nivel"
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# E/S de bajo nivel
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas funciones del sistema operativo directamente para la operación de nivel inferior que lo proporcionada por E\/S de secuencia.  Las llamadas de bajo nivel de entrada y salida no codifique los datos del búfer o de formato.  
  
 Las rutinas de bajo nivel pueden tener acceso a las secuencias estándar abierto en el inicio del programa mediante descriptores de archivo predefinidos siguientes.  
  
|Stream|Descriptor de archivo|  
|------------|---------------------------|  
|`stdin`|0|  
|`stdout`|1|  
|`stderr`|2|  
  
 Las rutinas de E\/S de bajo nivel establecen la variable global de [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) cuando se produce un error.  Debe incluir STDIO.H cuando se usan funciones de bajo nivel sólo si el programa requiere una constante que se define en STDIO.H, como la marca de fin de archivo \(`EOF`\).  
  
### Funciones de E\/S de bajo nivel  
  
|Función|Utilice|  
|-------------|-------------|  
|[\_close](../c-runtime-library/reference/close.md)|Archivo próximo|  
|[\_commit](../c-runtime-library/reference/commit.md)|Archivo alineado en el disco|  
|[\_creat, \_wcreat](../c-runtime-library/reference/creat-wcreat.md)|Cree el archivo|  
|[\_dup](../c-runtime-library/reference/dup-dup2.md)|Descriptor de archivo disponible siguiente return para el archivo especificado|  
|[\_dup2](../c-runtime-library/reference/dup-dup2.md)|Cree segundo descriptor para el archivo especificado|  
|[\_eof](../c-runtime-library/reference/eof.md)|Pruebe el final de archivo|  
|[\_lseek, \_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Coloque el puntero de archivo a la ubicación especificada|  
|[\_open, \_wopen](../c-runtime-library/reference/open-wopen.md)|Archivo abierto|  
|[\_read](../c-runtime-library/reference/read.md)|Leer datos desde el archivo|  
|[\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md), [\_sopen\_s, \_wsopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Archivo abierto para el uso compartido de archivos|  
|[\_tell, \_telli64](../c-runtime-library/reference/tell-telli64.md)|Obtenga la posición actual del archivo \(el archivo puntero|  
|[\_umask](../c-runtime-library/reference/umask.md), [\_umask\_s](../c-runtime-library/reference/umask-s.md)|Establezca la máscara de archivo|  
|[\_write](../c-runtime-library/reference/write.md)|Escribir datos en el archivo|  
  
 `_dup` y `_dup2` se utilizan normalmente para asociar los descriptores de archivo predefinidos con archivos diferentes.  
  
## Vea también  
 [Entrada y salida](../c-runtime-library/input-and-output.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Llamadas del sistema](../c-runtime-library/system-calls.md)