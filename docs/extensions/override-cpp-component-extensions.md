---
title: override  (C++/CLI and C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 32c825539efe670528eab7416afefe07d4cb1b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172105"
---
# <a name="override--ccli-and-ccx"></a>override  (C++/CLI and C++/CX)

La palabra clave contextual **override** indica que un miembro de un tipo invalida una clase base o un miembro de interfaz base.

## <a name="remarks"></a>Observaciones

La palabra clave **override** es válida al compilar para destinos nativos (opción del compilador predeterminada), destinos de Windows Runtime (opción del compilador `/ZW`) o destinos de Common Language Runtime (opción de compilador `/clr`).

Para más información sobre los especificadores de invalidación, consulte [Especificadores de invalidación](../cpp/override-specifier.md) y [Especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Para más información sobre las palabras clave contextuales, consulte [Palabras clave contextuales](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra que **override** también se puede usar en compilaciones nativas.

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que **override** se puede usar en compilaciones de Windows Runtime.

```cpp
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que **override** se puede usar en compilaciones de Common Language Runtime.

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Consulte también

[override (Especificador)](../cpp/override-specifier.md)<br/>
[Especificadores de invalidación](override-specifiers-cpp-component-extensions.md)
