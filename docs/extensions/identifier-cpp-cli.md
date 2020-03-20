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
ms.openlocfilehash: 395f1443f4eef16d9eea44c23a6e3288daf03d14
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545472"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Habilita el uso de palabras clave de C++ como identificadores.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="syntax"></a>Sintaxis

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Observaciones

Se permite el uso de la palabra clave **__identifier** para los identificadores que no son palabras clave, pero se desaconseja totalmente como cuestión de estilo.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="examples"></a>Ejemplos

**Ejemplo**

En el siguiente ejemplo, una clase llamada **template** se crea en C# y se distribuye como DLL. En el programa de C++/CLI que usa la clase **template**, la palabra clave **__identifier** oculta el hecho de que **template** es una palabra clave de C++ estándar.

```csharp
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

### <a name="remarks"></a>Observaciones

La palabra clave **__identifier** es válida con la opción del compilador `/clr`.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el siguiente ejemplo, una clase llamada **template** se crea en C# y se distribuye como DLL. En el programa de C++/CLI que usa la clase **template**, la palabra clave **__identifier** oculta el hecho de que **template** es una palabra clave de C++ estándar.

```csharp
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

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)<br/>
[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)