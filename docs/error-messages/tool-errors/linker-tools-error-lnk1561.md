---
title: Error de las herramientas del vinculador LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: ad216c7b7a09b8dd5d2ca2b86bc3a386fa18a552
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552820"
---
# <a name="linker-tools-error-lnk1561"></a>Error de las herramientas del vinculador LNK1561

se debe definir el punto de entrada

El vinculador no encontró un *punto de entrada*, la función inicial para llamar a en el archivo ejecutable. De forma predeterminada, el vinculador busca un `main` o `wmain` función para una aplicación de consola, un `WinMain` o `wWinMain` función para una aplicación de Windows, o `DllMain` para un archivo DLL que requiere inicialización. Puede especificar otra función mediante la [/Entry](../../build/reference/entry-entry-point-symbol.md) opción del vinculador.

Este error puede tener varias causas:
- No puede haber incluido el archivo que define el punto de entrada en la lista de archivos que se va a vincular. Compruebe que el archivo que contiene la función de punto de entrada está vinculado a la aplicación.
- Es posible que haya definido el punto de entrada mediante la firma de función incorrecto; Por ejemplo, se puede han mal escrito o usa el caso incorrecto para el nombre de función o especifica el tipo de valor devuelto o los tipos de parámetro incorrectamente.
- No puede haber especificado la [/DLL](../../build/reference/dll-build-a-dll.md) opción al crear un archivo DLL.
- Puede haber especificado el nombre de la función de punto de entrada incorrectamente cuando usa el [/Entry](../../build/reference/entry-entry-point-symbol.md) opción del vinculador.
- Si usas el [LIB](../../build/reference/lib-reference.md) herramienta para generar un archivo DLL, es posible que haya especificado un archivo .def. Si es así, quite el archivo .def la compilación.

Al compilar una aplicación, el vinculador busca una función de punto de entrada debe llamar para iniciar el código. Se trata de la función que se llama después de que se cargue la aplicación y se inicializa el tiempo de ejecución. Debe proporcionar una función de punto de entrada para una aplicación o no se puede ejecutar la aplicación. Un punto de entrada es opcional para un archivo DLL. De forma predeterminada, el vinculador busca una función de punto de entrada que tiene uno de varios nombres específicos y las firmas, como `int main(int, char**)`. Puede especificar otro nombre de función como la entrada de punto mediante la opción de vinculador/ENTRY.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```