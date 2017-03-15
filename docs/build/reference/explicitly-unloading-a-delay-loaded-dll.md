---
title: "Descargar expl&#237;citamente un archivo DLL de carga retrasada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAY:UNLOAD (opción del vinculador)"
  - "__FUnloadDelayLoadedDLL2"
  - "DELAY:UNLOAD (opción del vinculador)"
  - "carga retrasada de archivos DLL, descargar"
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Descargar expl&#237;citamente un archivo DLL de carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción de vinculador [\/delay](../../build/reference/delay-delay-load-import-settings.md):unload permite descargar un archivo DLL de carga retrasada.  De forma predeterminada, cuando el código descarga la DLL \(mediante \/delay:unload y **\_\_FUnloadDelayLoadedDLL2**\), las importaciones de carga retrasada permanecen en la tabla de direcciones de importación \(IAT\).  Sin embargo, si se utiliza el modificador \/delay:unload en la línea de comandos del vinculador, la función auxiliar admitirá la descarga explícita del archivo DLL, restableciendo el formato original en la tabla IAT; se sobrescribirán los punteros que no son válidos actualmente.  La tabla IAT es un campo de [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) que contiene la dirección de una copia de la tabla IAT original \(si existe\).  
  
## Ejemplo  
  
### Código  
  
```  
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD  
#include <windows.h>  
#include <delayimp.h>  
#include "MyDll.h"  
#include <stdio.h>  
  
#pragma comment(lib, "delayimp")  
#pragma comment(lib, "MyDll")  
int main()  
{  
    BOOL TestReturn;  
    // MyDLL.DLL will load at this point  
    fnMyDll();  
  
    //MyDLL.dll will unload at this point  
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");  
  
    if (TestReturn)  
        printf_s("\nDLL was unloaded");  
    else  
        printf_s("\nDLL was not unloaded");  
}  
```  
  
### Comentarios  
 Notas importantes sobre la descarga de una DLL de carga retrasada:  
  
-   La implementación de la función **\_\_FUnloadDelayLoadedDLL2** se puede encontrar en el archivo \\VC7\\INCLUDE\\DELAYHLP.CPP.  
  
-   El parámetro de nombre de la función **\_\_FUnloadDelayLoadedDLL2** debe coincidir exactamente \(incluidas mayúsculas y minúsculas\) con el contenido de la biblioteca de importación \(esa cadena se encuentra también en la tabla de importación de la imagen\).  Puede ver el contenido de la biblioteca de importación mediante [DUMPBIN \/DEPENDENTS](../../build/reference/dependents.md).  Si se desea una coincidencia de cadenas sin distinguir entre mayúsculas y minúsculas, puede actualizar **\_\_FUnloadDelayLoadedDLL2** para que utilice una de las funciones de cadena CRT o una llamada API de Windows.  
  
 Vea [Descargar un archivo DLL de carga retrasada](../../build/reference/unloading-a-delay-loaded-dll.md) para obtener más información.  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)