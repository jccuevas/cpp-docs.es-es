---
title: Error de las herramientas del vinculador LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: e55202274c5ec3982f784ad6cdf074a5a99e922f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491395"
---
# <a name="linker-tools-error-lnk2022"></a>Error de las herramientas del vinculador LNK2022

> Error de la operación de metadatos (*HRESULT*): *error_message*

El vinculador detectó un error al combinar los metadatos. Para vincular correctamente, se deben resolver los errores de metadatos.

Una forma de diagnosticar el problema es ejecutar **ildasm-tokens** en los archivos objeto para averiguar qué tipos tienen los tokens se enumeran en `error_message`y ver las diferencias.  En los metadatos, los dos tipos diferentes con el mismo nombre no es válido, incluso si el atributo LayoutType es diferente.

Una razón para LNK2022 es cuando un tipo (por ejemplo, un struct) existe en varias operaciones de compilación con el mismo nombre pero con definiciones en conflicto, y cuando se compila con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  En este caso, asegúrese de que el tipo tiene una definición idéntica en todos los elementos.  Aparece el nombre de tipo en `error_message`.

Otra causa posible de LNK2022 es cuando el vinculador busca un archivo de metadatos en una ubicación diferente que no se especificó para el compilador (con [#using](../../preprocessor/hash-using-directive-cpp.md) ). Asegúrese de que el archivo de metadatos (.dll o .netmodule) está en la misma ubicación cuando se pasan al vinculador, igual que cuando que se pasó al compilador.

Al compilar una aplicación ATL, el uso de la macro `_ATL_MIXED` se requiere en todos los elementos, si se usa en al menos uno.

## <a name="example"></a>Ejemplo

El ejemplo siguiente define un tipo vacío.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>Ejemplo

Este ejemplo muestra que no se puede vincular dos archivos de código fuente que contienen tipos del mismo nombre pero definiciones diferentes.

El ejemplo siguiente genera el error LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```