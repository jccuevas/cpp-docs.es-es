---
title: Compilador advertencia (nivel 1) C4462 | Documentos de Microsoft
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C4462
dev_langs: C++
helpviewer_keywords: C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c3f125224832002e3ae962b75e4b770cd766b21
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-level-1-c4462"></a>Advertencia del compilador (nivel 1) C4462

> no puede determinar el GUID del tipo. El programa puede dar un error en tiempo de ejecución.

La advertencia C4462 se produce en una aplicación o componente de Windows en tiempo de ejecución cuando uno de los parámetros de tipos de un controlador `TypedEventHandler` público es una referencia a la clase envolvente.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md). Por ejemplo, para convertir C4462 en un problema de la advertencia de nivel 4, agregue esta línea al archivo de código fuente:

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Ejemplo

Este ejemplo genera la advertencia C4462:

```cpp
namespace N
{
       public ref struct EventArgs sealed {};
       public ref struct R sealed
       {
              R() {}
              event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
       };
}

[Platform::MTAThread]
int main()
{
     auto x = ref new N::R();
}
```

Hay dos maneras de evitar el error. Una de ellas, la que se muestra en el ejemplo siguiente, es proporcionar al evento accesibilidad interna, de modo que esté disponible para el código que se encuentra en el mismo ejecutable pero no para el código de otros componentes de Windows en tiempo de ejecución.

```cpp
internal:
    event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
```

Si el evento tiene que ser público, puede utilizar la otra solución, que consiste en exponerlo a través de una interfaz predeterminada:

```cpp
ref struct R;
public interface struct IR{ event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;};

public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR
{
    R() {}
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
};
```

Un GUID del tipo `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` solo se utiliza cuando se accede al tipo desde otro componente. La primera solución funciona porque, tras implementarla, solo puede acceder dentro de su propio componente. De lo contrario, el compilador tendría que presuponer el peor de los casos y emitir la advertencia.
