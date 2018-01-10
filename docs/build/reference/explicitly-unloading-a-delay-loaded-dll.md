---
title: "Descargar explícitamente una archivo DLL de carga retrasada | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b26a1a17952693be9db6a80649aad2c40227d53e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Descargar explícitamente un archivo DLL de carga retrasada
El [/delay](../../build/reference/delay-delay-load-import-settings.md): opción de vinculador unload permite descargar un archivo DLL de carga retrasada. De forma predeterminada, cuando el código descarga la DLL (mediante/delay: unload y **__FUnloadDelayLoadedDLL2**), las importaciones de carga retrasada permanecen en la tabla de direcciones de importación (IAT). Sin embargo, si utiliza/Delay: Unload en la línea de comandos del vinculador, la función auxiliar admitirá la descarga explícita de la DLL, restableciendo la IAT a su forma original; se sobrescribirán los punteros no son válidos ahora. La tabla IAT es un campo en el [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) que contiene la dirección de una copia de la tabla IAT original (si existe).  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
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
  
### <a name="comments"></a>Comentarios  
 Notas importantes sobre la descarga de un archivo DLL de carga retrasada:  
  
-   Puede encontrar la implementación de la **__FUnloadDelayLoadedDLL2** función en el archivo \VC7\INCLUDE\DELAYHLP. CPP.  
  
-   El parámetro de nombre de la **__FUnloadDelayLoadedDLL2** función debe coincidir exactamente con (incluidas las mayúsculas) lo que la biblioteca de importación contiene (esa cadena se encuentra también en la tabla de importación de la imagen). Puede ver el contenido de la biblioteca de importación con [DUMPBIN /DEPENDENTS](../../build/reference/dependents.md). Si se desea una coincidencia de cadenas entre mayúsculas y minúsculas, puede actualizar **__FUnloadDelayLoadedDLL2** utilizar una de las funciones de cadena CRT o una llamada de API de Windows.  
  
 Vea [descargar un archivo DLL de carga retrasada](../../build/reference/unloading-a-delay-loaded-dll.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)