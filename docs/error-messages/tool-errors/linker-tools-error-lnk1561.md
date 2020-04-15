---
title: Error de las herramientas del vinculador LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357749"
---
# <a name="linker-tools-error-lnk1561"></a>Error de las herramientas del vinculador LNK1561

punto de entrada debe definirse

El vinculador no encontró un punto de *entrada,* la función inicial para llamar en el ejecutable. De forma predeterminada, el `main` vinculador `wmain` busca una o `WinMain` `wWinMain` función para una aplicación de consola, una o función para una aplicación de Windows o `DllMain` un archivo DLL que requiere inicialización. Puede especificar otra función mediante la opción del vinculador [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)

Este error puede tener varias causas:

- Es posible que no haya incluido el archivo que define el punto de entrada en la lista de archivos que se van a vincular. Compruebe que el archivo que contiene la función de punto de entrada está vinculado a la aplicación.
- Es posible que haya definido el punto de entrada utilizando la firma de función incorrecta; por ejemplo, puede haber escrito mal o utilizado el caso incorrecto para el nombre de la función, o especificado el tipo de valor devuelto o los tipos de parámetro incorrectamente.
- Es posible que no haya especificado la opción [/DLL](../../build/reference/dll-build-a-dll.md) al compilar un archivo DLL.
- Es posible que haya especificado el nombre de la función de punto de entrada incorrectamente cuando utilizó la opción del vinculador [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)
- Si utiliza la herramienta [LIB](../../build/reference/lib-reference.md) para crear un archivo DLL, es posible que haya especificado un archivo .def. Si es así, quite el archivo .def de la compilación.

Al compilar una aplicación, el vinculador busca una función de punto de entrada para llamar para iniciar el código. Esta es la función a la que se llama después de cargar la aplicación y inicializar el tiempo de ejecución. Debe proporcionar una función de punto de entrada para una aplicación o la aplicación no se puede ejecutar. Un punto de entrada es opcional para un archivo DLL. De forma predeterminada, el vinculador busca una función de punto de `int main(int, char**)`entrada que tenga uno de varios nombres y firmas específicos, como . Puede especificar otro nombre de función como punto de entrada mediante la opción del vinculador /ENTRY.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
