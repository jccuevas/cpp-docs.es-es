---
title: Importar llamadas a funciones mediante __declspec (dllimport) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1239ee3b33a9d6c8443161bacae6daea20260c1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368540"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Importar llamadas a funciones mediante __declspec(dllimport)
En el ejemplo de código siguiente se muestra cómo utilizar **_declspec (dllimport)** para importar llamadas a funciones desde un archivo DLL a una aplicación. Se asume que `func1` es una función que reside en un archivo DLL independiente del archivo .exe que contiene el **principal** función.  
  
 Sin **__declspec (dllimport)**, dado el código:  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 el compilador genera código que el siguiente aspecto:  
  
```  
call func1  
```  
  
 y el vinculador traducirá la llamada en algo parecido a esto:  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 Si `func1` existe en otro archivo DLL, el vinculador no puede resolver directamente porque no tiene ninguna manera de saber qué la dirección de `func1` es. En entornos de 16 bits, el vinculador agrega esta dirección de código a una lista en el archivo .exe que el cargador revisaría en tiempo de ejecución con la dirección correcta. En entornos de 32 bits y 64 bits, el vinculador genera un código thunk de los cuales conoce la dirección. En un entorno de 32 bits, el código thunk es similar:  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 Aquí `imp_func1` es la dirección para el `func1` ranura en la tabla de direcciones de importación del archivo .exe. Por lo tanto, todas las direcciones se conocen como el vinculador. El cargador sólo tiene que actualizar la tabla de direcciones de importación del archivo .exe en tiempo de carga para que todo funcione correctamente.  
  
 Por tanto, se usan **__declspec (dllimport)** es mejor porque el vinculador no genera un código thunk si no es necesario. Fragmentos de código thunk que el código sea mayor (en sistemas RISC, pueden ser varias instrucciones) y puede degradar el rendimiento de la memoria caché. Si indica al compilador que la función está en un archivo DLL, puede generar una llamada indirecta.  
  
 Ahora este código:  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 genera la siguiente instrucción:  
  
```  
call DWORD PTR __imp_func1  
```  
  
 No hay ningún código thunk pero no `jmp` instrucciones, por lo que el código es más pequeñas y rápidas.  
  
 Por otro lado, para las llamadas de función dentro de un archivo DLL, no desea que deba utilizar una llamada indirecta. Ya sabe dirección de una función. Dado que se requiere tiempo y espacio para cargar y almacenar la dirección de la función antes de una llamada indirecta, una llamada directa siempre es más rápido y más pequeños. Desea usar **__declspec (dllimport)** al llamar a funciones DLL desde fuera el propio archivo DLL. No utilice **__declspec (dllimport)** en funciones dentro de un archivo DLL cuando genere dicho archivo DLL.  
  
## <a name="see-also"></a>Vea también  
 [Importación a una aplicación](../build/importing-into-an-application.md)