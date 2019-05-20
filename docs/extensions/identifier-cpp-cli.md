---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 80aade53bf1d1c9aa30c4b8c8fe59c2247fe3cfb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515790"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

Habilita el uso de palabras clave de C++ como identificadores.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="syntax"></a>Sintaxis

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Comentarios

Se permite el uso de la palabra clave **__identifier** para los identificadores que no son palabras clave, pero se desaconseja totalmente como cuestión de estilo.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="examples"></a>Ejemplos

**Ejemplo**

En el siguiente ejemplo, una clase llamada **template** se crea en C# y se distribuye como DLL. En el programa de C++/CLI que usa la clase **template**, la palabra clave **__identifier** oculta el hecho de que **template** es una palabra clave de C++ estándar.

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

La palabra clave **__identifier** es válida con la opción del compilador `/clr`.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el siguiente ejemplo, una clase llamada **template** se crea en C# y se distribuye como DLL. En el programa de C++/CLI que usa la clase **template**, la palabra clave **__identifier** oculta el hecho de que **template** es una palabra clave de C++ estándar.

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)<br/>
[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)