---
title: Advertencia del compilador (nivel 1) C4462
ms.date: 10/25/2017
f1_keywords:
- C4462
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
ms.openlocfilehash: bd4d5c1fd7dd8d7419fc901149ceab7e769e7076
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331872"
---
# <a name="compiler-warning-level-1-c4462"></a>Advertencia del compilador (nivel 1) C4462

> no puede determinar el GUID del tipo. El programa puede dar un error en tiempo de ejecución.

La advertencia C4462 se produce en una aplicación o componente de Windows Runtime cuando uno de los parámetros de tipos de un controlador `TypedEventHandler` público es una referencia a la clase envolvente.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md). Por ejemplo, para C4462 en una advertencia de nivel 4, agregue esta línea al archivo de código fuente:

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
