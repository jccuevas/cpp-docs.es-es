---
title: "_getdiskfree | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getdiskfree"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "getdiskfree"
  - "_getdiskfree"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_diskfree_t (tipo)"
  - "_getdiskfree (función)"
  - "tamaño de disco"
  - "diskfree_t (tipo)"
  - "getdiskfree (función)"
ms.assetid: 47a3f6cf-4816-452a-8f3d-1c3ae02a0f2a
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdiskfree
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Usa la información sobre una unidad de disco para rellenar una estructura `_diskfree_t`.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned _getdiskfree(  
   unsigned drive,  
   struct _diskfree_t * driveinfo  
);  
```  
  
#### Parámetros  
 \[in\] `drive`  
 Unidad de disco de la que desea obtener información.  
  
 \[out\] `driveinfo`  
 Estructura `_diskfree_t` que se rellenará con información de la unidad.  
  
## Valor devuelto  
 Si la función es correcta, el valor devuelto es cero.  Si la función no es correcta, el valor devuelto es un código de error.  El valor `errno` se establece para los errores devueltos por el sistema operativo.  Para obtener más información sobre las condiciones de error que se indican mediante `errno`, vea [errno \(Constantes\)](../../c-runtime-library/errno-constants.md).  
  
## Comentarios  
 La estructura `_diskfree_t` se define en Direct.h.  
  
```  
struct _diskfree_t {   
   unsigned total_clusters;   
   unsigned avail_clusters;   
   unsigned sectors_per_cluster;   
   unsigned bytes_per_sector;   
};  
```  
  
 Esta función valida sus parámetros.  Si el puntero `driveinfo` es `NULL` o `drive` especifica una unidad no válida, esta función invoca un controlador de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `EINVAL` y establece en `errno` en `EINVAL`.  Las unidades válidas oscilan entre 0 y 26.  Un valor 0 en `drive` especifica la unidad actual; a partir de ahí, se asignan números a letras del alfabeto inglés de forma tal que 1 es la unidad A, 3 es la unidad C, y así sucesivamente.  
  
 `total_clusters`  
 Número total de clústeres, tanto en uso como disponibles, en el disco.  
  
 `avail_clusters`  
 Número de clústeres sin usar en el disco.  
  
 `sectors_per_cluster`  
 Número de sectores en cada clúster.  
  
 `bytes_per_sector`  
 Tamaño de cada sector en bytes.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getdiskfree`|\<direct.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getdiskfree.c  
// compile with: /c  
#include <windows.h>  
#include <direct.h>  
#include <stdio.h>  
#include <tchar.h>  
  
TCHAR   g_szBorder[] = _T("======================================================================\n");  
TCHAR   g_szTitle1[] = _T("|DRIVE|TOTAL CLUSTERS|AVAIL CLUSTERS|SECTORS / CLUSTER|BYTES / SECTOR|\n");  
TCHAR   g_szTitle2[] = _T("|=====|==============|==============|=================|==============|\n");  
TCHAR   g_szLine[]   = _T("|  A: |              |              |                 |              |\n");  
  
void utoiRightJustified(TCHAR* szLeft, TCHAR* szRight, unsigned uVal);  
  
int main(int argc, char* argv[]) {  
   TCHAR szMsg[4200];  
   struct _diskfree_t df = {0};  
   ULONG uDriveMask = _getdrives();  
   unsigned uErr, uLen, uDrive;  
  
   printf(g_szBorder);  
   printf(g_szTitle1);  
   printf(g_szTitle2);  
  
   for (uDrive=1; uDrive<=26; ++uDrive) {  
      if (uDriveMask & 1) {  
         uErr = _getdiskfree(uDrive, &df);  
         memcpy(szMsg, g_szLine, sizeof(g_szLine));  
         szMsg[3] = uDrive + 'A' - 1;  
  
         if (uErr == 0) {  
            utoiRightJustified(szMsg+8,  szMsg+19, df.total_clusters);  
            utoiRightJustified(szMsg+23, szMsg+34, df.avail_clusters);  
            utoiRightJustified(szMsg+38, szMsg+52, df.sectors_per_cluster);  
            utoiRightJustified(szMsg+56, szMsg+67, df.bytes_per_sector);  
         }  
         else {  
            uLen = FormatMessage(FORMAT_MESSAGE_FROM_SYSTEM, NULL,  
                            uErr, 0, szMsg+8, 4100, NULL);  
            szMsg[uLen+6] = ' ';  
            szMsg[uLen+7] = ' ';  
            szMsg[uLen+8] = ' ';  
         }  
  
         printf(szMsg);  
      }  
  
      uDriveMask >>= 1;  
   }  
  
   printf(g_szBorder);  
}  
  
void utoiRightJustified(TCHAR* szLeft, TCHAR* szRight, unsigned uVal) {  
   TCHAR* szCur = szRight;  
   int nComma = 0;  
  
   if (uVal) {  
      while (uVal && (szCur >= szLeft)) {  
         if   (nComma == 3) {  
            *szCur = ',';  
            nComma = 0;  
         }  
         else {  
            *szCur = (uVal % 10) | 0x30;  
            uVal /= 10;  
            ++nComma;  
         }  
  
         --szCur;  
      }  
   }  
   else {  
      *szCur = '0';  
      --szCur;  
   }  
  
   if (uVal) {  
      szCur = szLeft;  
  
      while   (szCur <= szRight) {  
         *szCur = '*';  
         ++szCur;  
      }  
   }  
}  
```  
  
  **\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=**  
**&#124;DRIVE&#124;TOTAL CLUSTERS&#124;AVAIL CLUSTERS&#124;SECTORS \/ CLUSTER&#124;BYTES \/ SECTOR&#124;**  
**&#124;\=\=\=\=\=&#124;\=\=\=\=\=\=\=\=\=\=\=\=\=\=&#124;\=\=\=\=\=\=\=\=\=\=\=\=\=\=&#124;\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=&#124;\=\=\=\=\=\=\=\=\=\=\=\=\=\=&#124;**  
**&#124;  A: &#124; El dispositivo no está preparado.  &#124;                 &#124;              &#124;**  
**&#124;  C: &#124;    4,721,093 &#124;    3,778,303 &#124;               8 &#124;          512 &#124;**  
**&#124;  D: &#124;    1,956,097 &#124;    1,800,761 &#124;               8 &#124;          512 &#124;**  
**&#124;  E: &#124; El dispositivo no está preparado.  &#124;                 &#124;              &#124;**  
**\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=\=**    
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)