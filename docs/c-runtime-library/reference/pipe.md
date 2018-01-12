---
title: _pipe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _pipe
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- pipe
- _pipe
dev_langs: C++
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a14fa401b2a46bbfb3d5aafcda4d05c0167b3d9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pipe"></a>_pipe
Crear una canalización de lectura y escritura.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _pipe(  
   int *pfds,  
   unsigned int psize,  
   int textmode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfds`[2]  
 Matriz que va a contener descriptores de archivo de lectura y escritura.  
  
 `psize`  
 Cantidad de memoria que se va a reservar.  
  
 `textmode`  
 Modo de archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve 0. Devuelve -1 para indicar un error. Si se produce un error, `errno` se establece en uno de estos valores:  
  
-   `EMFILE`, que indica que no hay más descriptores de archivo disponibles.  
  
-   `ENFILE`, que indica un desbordamiento de tabla de sistema de archivos.  
  
-   `EINVAL`, que indica que la matriz `pfds` es un puntero nulo o que se ha pasado un valor no válido para `textmode`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_pipe` crea una *canalización*, un canal de E/S artificial que un programa usa para pasar información a otros programas. Una canalización se parece a un archivo porque tiene un puntero de archivo, un descriptor de archivo, o las dos cosas, y con se puede leer o escribir mediante las funciones de entrada y salida estándar de la biblioteca estándar. Sin embargo, una canalización no representa un archivo o un dispositivo específico. En lugar de ello, representa almacenamiento temporal en memoria que es independiente de la propia memoria del programa y que el sistema operativo controla totalmente.  
  
 `_pipe` se parece a `_open`, pero abre la canalización para lectura y escritura, y devuelve dos descriptores de archivo en lugar de uno. El programa puede usar los dos extremos de la canalización, o cerrar la que no necesita. Por ejemplo, el procesador de comandos de Windows crea una canalización cuando ejecuta un comando como `PROGRAM1 | PROGRAM2`.  
  
 El descriptor de salida estándar de `PROGRAM1` se adjunta al descriptor de escritura de la canalización. El descriptor de entrada estándar de `PROGRAM2` se adjunta al descriptor de lectura de la canalización. Así no es necesario crear archivos temporales para pasar información a otros programas.  
  
 La función `_pipe` devuelve dos descriptores de archivo de la canalización en el argumento `pfds`. El elemento `pfds`[0] contiene el descriptor de lectura y el elemento `pfds`[1] contiene el descriptor de escritura. Los descriptores de archivo de canalización se usan de la misma forma que otros descriptores de archivo. (Las funciones de entrada y salida de nivel inferior `_read` y `_write` pueden leer una canalización y escribir en ella.) Para detectar la condición de final de canalización, compruebe si hay una solicitud de `_read` que devuelve 0 como número de bytes leídos.  
  
 El argumento `psize` especifica la cantidad de memoria, en bytes, que se va a reservar para la canalización. El argumento `textmode` especifica el modo de traducción de la canalización. La constante de manifiesto `_O_TEXT` especifica una traducción de texto, y la constante `_O_BINARY` especifica la traducción binaria. (Vea [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md) para ver una descripción de los modos de texto y binario.) Si el argumento `textmode` es 0, `_pipe` usa el modo de traducción predeterminado especificado por la variable [_fmode](../../c-runtime-library/fmode.md) de modo predeterminado.  
  
 En programas multiproceso, no se realiza ningún bloqueo. Los descriptores de archivo que se devuelven se han abierto recientemente y ningún subproceso debe hacer referencia a ellos hasta que se complete la llamada a `_pipe`.  
  
 Para usar la función `_pipe` para la comunicación entre un proceso primario y un proceso secundario, cada proceso solo debe tener solo un descriptor abierto en la canalización. Los descriptores deben ser opuestos: si el elemento primario tiene un descriptor de lectura abierto, el elemento secundario debe tener abierto un descriptor de escritura. La manera más fácil de hacerlo consiste en usar `OR` (`|`) con la marca `_O_NOINHERIT` con `textmode`. A continuación, use `_dup` o `_dup2` para crear una copia heredable del descriptor de la canalización que desee pasar al elemento secundario. Cierre el descriptor original y, a continuación, genere el proceso secundario. Después de la llamada de generación, cierre el descriptor duplicado en el proceso primario. Para obtener más información, vea el ejemplo 2 que figura más adelante en este artículo.  
  
 En el sistema operativo Windows, una canalización se destruye cuando se han cerrado todos sus descriptores. (Cuando se han cerrado todos los descriptores de lectura en la canalización, si se escribe en la canalización se produce un error). Todas las operaciones de lectura y escritura en la canalización esperan hasta que hay suficientes datos o suficiente espacio en búfer para llevar a cabo la solicitud de E/S.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_pipe`|\<io.h>|\<fcntl.h>,1 \<errno.h>2|  
  
 1 Para las definiciones de `_O_BINARY` y `_O_TEXT`.  
  
 2 Definiciones de `errno`.  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example-1"></a>Ejemplo 1  
  
```C  
// crt_pipe.c  
/* This program uses the _pipe function to pass streams of  
 * text to spawned processes.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <io.h>  
#include <fcntl.h>  
#include <process.h>  
#include <math.h>  
  
enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */  
#define NUMPROBLEM 8  
  
int main( int argc, char *argv[] )  
{  
  
   int fdpipe[2];  
   char hstr[20];  
   int pid, problem, c;  
   int termstat;  
  
   /* If no arguments, this is the spawning process */  
   if( argc == 1 )  
   {  
  
      setvbuf( stdout, NULL, _IONBF, 0 );  
  
      /* Open a set of pipes */  
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )  
          exit( 1 );  
  
      /* Convert pipe read descriptor to string and pass as argument   
       * to spawned program. Program spawns itself (argv[0]).  
       */  
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );  
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],   
            hstr, NULL ) ) == -1 )  
          printf( "Spawn failed" );  
  
      /* Put problem in write pipe. Since spawned program is   
       * running simultaneously, first solutions may be done   
       * before last problem is given.  
       */  
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)  
      {  
  
         printf( "Son, what is the square root of %d?\n", problem );  
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );  
  
      }  
  
      /* Wait until spawned program is done processing. */  
      _cwait( &termstat, pid, WAIT_CHILD );  
      if( termstat & 0x0 )  
         printf( "Child failed\n" );  
  
      _close( fdpipe[READ] );  
      _close( fdpipe[WRITE] );  
  
   }  
  
   /* If there is an argument, this must be the spawned process. */  
   else  
   {  
  
      /* Convert passed string descriptor to integer descriptor. */  
      fdpipe[READ] = atoi( argv[1] );  
  
      /* Read problem from pipe and calculate solution. */  
      for( c = 0; c < NUMPROBLEM; c++ )  
      {  
  
        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );  
        printf( "Dad, the square root of %d is %3.2f.\n",  
                 problem, sqrt( ( double )problem ) );  
  
      }  
   }  
}  
```  
  
```Output  
Son, what is the square root of 1000?  
Son, what is the square root of 2000?  
Son, what iDad, the square root of 1000 is 31.62.  
Dad, the square root of 2000 is 44.72.  
s the square root of 3000?  
Dad, the square root of 3000 is 54.77.  
Son, what is the square root of 4000?  
Dad, the square root of 4000 is 63.25.  
Son, what is the square root of 5000?  
Dad, the square root of 5000 is 70.71.  
Son, what is the square root of 6000?  
SonDad, the square root of 6000 is 77.46.  
, what is the square root of 7000?  
Dad, the square root of 7000 is 83.67.  
Son, what is the square root of 8000?  
Dad, the square root of 8000 is 89.44.  
```  
  
## <a name="example-2"></a>Ejemplo 2  
 Se trata de una aplicación de filtro básica. Genera el crt_pipe_beeper de la aplicación después de crear una canalización que dirige al filtro el stdout de la aplicación generado. El filtro quita caracteres ASCII 7 (beep).  
  
```C  
// crt_pipe_beeper.c  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   int   i;  
   for(i=0;i<10;++i)  
      {  
         printf("This is speaker beep number %d...\n\7", i+1);  
      }  
   return 0;  
}  
```  
  
 La aplicación de filtro es:  
  
```C  
// crt_pipe_BeepFilter.C  
// arguments: crt_pipe_beeper.exe  
  
#include <windows.h>  
#include <process.h>  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
#define   OUT_BUFF_SIZE 512  
#define   READ_FD 0  
#define   WRITE_FD 1  
#define   BEEP_CHAR 7  
  
char szBuffer[OUT_BUFF_SIZE];  
  
int Filter(char* szBuff, ULONG nSize, int nChar)  
{  
   char* szPos = szBuff + nSize -1;  
   char* szEnd = szPos;  
   int nRet = nSize;  
  
   while (szPos > szBuff)  
   {  
      if (*szPos == nChar)  
         {  
            memmove(szPos, szPos+1, szEnd - szPos);  
            --nRet;  
         }  
      --szPos;  
   }  
   return nRet;  
}  
  
int main(int argc, char** argv)  
{  
   int nExitCode = STILL_ACTIVE;  
   if (argc >= 2)  
   {  
      HANDLE hProcess;  
      int fdStdOut;  
      int fdStdOutPipe[2];  
  
      // Create the pipe  
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)  
         return   1;  
  
      // Duplicate stdout file descriptor (next line will close original)  
      fdStdOut = _dup(_fileno(stdout));  
  
      // Duplicate write end of pipe to stdout file descriptor  
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)  
         return   2;  
  
      // Close original write end of pipe  
      _close(fdStdOutPipe[WRITE_FD]);  
  
      // Spawn process  
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],   
       (const char* const*)&argv[1]);  
  
      // Duplicate copy of original stdout back into stdout  
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)  
         return   3;  
  
      // Close duplicate copy of original stdout  
      _close(fdStdOut);  
  
      if(hProcess)  
      {  
         int nOutRead;  
         while   (nExitCode == STILL_ACTIVE)  
         {  
            nOutRead = _read(fdStdOutPipe[READ_FD],   
             szBuffer, OUT_BUFF_SIZE);  
            if(nOutRead)  
            {  
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);  
               fwrite(szBuffer, 1, nOutRead, stdout);  
            }  
  
            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))  
               return 4;  
         }  
      }  
   }  
   return nExitCode;  
}  
```  
  
```Output  
This is speaker beep number 1...  
This is speaker beep number 2...  
This is speaker beep number 3...  
This is speaker beep number 4...  
This is speaker beep number 5...  
This is speaker beep number 6...  
This is speaker beep number 7...  
This is speaker beep number 8...  
This is speaker beep number 9...  
This is speaker beep number 10...  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)