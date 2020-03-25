---
title: Error de las herramientas del vinculador LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: 706cf6c90dc187b6c343edc82cebb93bb8660452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194855"
---
# <a name="linker-tools-error-lnk1561"></a>Error de las herramientas del vinculador LNK1561

se debe definir el punto de entrada

El vinculador no encontró un *punto de entrada*, la función inicial a la que se llamará en el archivo ejecutable. De forma predeterminada, el vinculador busca una función `main` o `wmain` para una aplicación de consola, una función `WinMain` o `wWinMain` para una aplicación de Windows o `DllMain` para un archivo DLL que requiere inicialización. Puede especificar otra función mediante la opción del vinculador [/entry](../../build/reference/entry-entry-point-symbol.md) .

Este error puede tener varias causas:
- Es posible que no haya incluido el archivo que define el punto de entrada en la lista de archivos que se van a vincular. Compruebe que el archivo que contiene la función de punto de entrada está vinculado a la aplicación.
- Es posible que haya definido el punto de entrada con una firma de función incorrecta. por ejemplo, es posible que haya escrito mal la grafía o que haya utilizado el nombre de la función, o que haya especificado incorrectamente el tipo de valor devuelto o los tipos de parámetro.
- Es posible que no haya especificado la opción [/dll](../../build/reference/dll-build-a-dll.md) al compilar un archivo dll.
- Es posible que haya especificado incorrectamente el nombre de la función de punto de entrada cuando se usó la opción del vinculador [/entry](../../build/reference/entry-entry-point-symbol.md) .
- Si usa la herramienta [lib](../../build/reference/lib-reference.md) para compilar un archivo dll, es posible que haya especificado un archivo. def. En ese caso, quite el archivo. def de la compilación.

Al compilar una aplicación, el vinculador busca una función de punto de entrada que llame a para iniciar el código. Esta es la función a la que se llama una vez que se carga la aplicación y se inicializa el tiempo de ejecución. Debe proporcionar una función de punto de entrada para una aplicación o no se puede ejecutar la aplicación. Un punto de entrada es opcional para un archivo DLL. De forma predeterminada, el vinculador busca una función de punto de entrada que tenga uno de varios nombres y firmas específicos, como `int main(int, char**)`. Puede especificar otro nombre de función como punto de entrada mediante la opción del enlazador/ENTRY.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
