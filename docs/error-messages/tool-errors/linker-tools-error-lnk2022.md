---
title: Error de las herramientas del vinculador LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: d30dad6f8ad146ff467eb4eaf32b21dd6950d25f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194647"
---
# <a name="linker-tools-error-lnk2022"></a>Error de las herramientas del vinculador LNK2022

> error en la operación de metadatos (*HRESULT*): *error_message*

El enlazador detectó un error al mezclar metadatos. Los errores de metadatos se deben resolver para vincularse correctamente.

Una manera de diagnosticar este problema es ejecutar **Ildasm-tokens** en los archivos objeto para buscar qué tipos tienen los tokens enumerados en `error_message`y buscar diferencias.  En los metadatos, dos tipos diferentes con el mismo nombre no son válidos, incluso si el atributo Just LayoutType es diferente.

Una razón para LNK2022 es cuando un tipo (como un struct) existe en varios compilandos con el mismo nombre, pero con definiciones en conflicto, y al compilar con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  En este caso, asegúrese de que el tipo tiene una definición idéntica en todos los compilandos.  El nombre del tipo se muestra en `error_message`.

Otra causa posible de LNK2022 es cuando el vinculador encuentra un archivo de metadatos en una ubicación diferente de la que se especificó en el compilador (con [#using](../../preprocessor/hash-using-directive-cpp.md) ). Asegúrese de que el archivo de metadatos (. dll o. netmodule) está en la misma ubicación cuando se pasa al enlazador, tal y como estaba cuando se pasó al compilador.

Al compilar una aplicación ATL, el uso de la macro `_ATL_MIXED` es necesario en todos los compilandos de elementos, si se utiliza en al menos uno.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define un tipo vacío.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>Ejemplo

Este ejemplo muestra que no se pueden vincular dos archivos de código fuente que contengan tipos del mismo nombre pero diferentes definiciones.

En el ejemplo siguiente se genera LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```
