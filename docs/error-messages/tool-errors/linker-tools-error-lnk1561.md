---
title: Las herramientas del vinculador LNK1561 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: f918c51e6f4539c020bc59ad28c867f8e2d1ae75
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk1561"></a>Error de las herramientas del vinculador LNK1561
se debe definir el punto de entrada  
  
El vinculador no encontró un *punto de entrada*, la función inicial se debe llamar en su archivo ejecutable. De forma predeterminada, el vinculador busca una `main` o `wmain` función para una aplicación de consola, una `WinMain` o `wWinMain` función para una aplicación de Windows, o `DllMain` para un archivo DLL que requiera una inicialización. Puede especificar otra función mediante el [/Entry](../../build/reference/entry-entry-point-symbol.md) opción del vinculador.  
  
Este error puede tener varias causas:  
-   Es podrán que no haya incluido el archivo que define el punto de entrada en la lista de archivos que se va a vincular. Compruebe que el archivo que contiene la función de punto de entrada está vinculado a la aplicación.  
-   Puede que haya definido el punto de entrada mediante la firma de función incorrecto; Por ejemplo, se puede ha mal escrito o usa el caso incorrecto para el nombre de función o especifica el tipo de valor devuelto o los tipos de parámetro incorrectamente.  
-   No puede haber especificado la [/DLL](../../build/reference/dll-build-a-dll.md) opción al crear un archivo DLL.  
-   Puede haber especificado el nombre de la función de punto de entrada incorrecto cuando usa el [/Entry](../../build/reference/entry-entry-point-symbol.md) opción del vinculador.  
-   Si usas el [LIB](../../build/reference/lib-reference.md) herramienta para generar un archivo DLL, puede haber un archivo .def especificado. Si es así, quite el archivo .def de la compilación.    
  
Al compilar una aplicación, el vinculador busca una función de punto de entrada debe llamar para iniciar el código. Se trata de la función que se llama una vez cargada la aplicación y se inicializa el tiempo de ejecución. Debe proporcionar una función de punto de entrada para una aplicación o no se puede ejecutar la aplicación. Un punto de entrada es opcional para un archivo DLL. De forma predeterminada, el vinculador busca una función de punto de entrada que tiene uno de los nombres específicos y firmas, como `int main(int, char**)`. Puede especificar otro nombre de función como la entrada punto mediante la opción de vinculador/ENTRY.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```
