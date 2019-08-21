---
title: Especificar la optimización del compilador para un proyecto ATL
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630610"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Especificar la optimización del compilador para un proyecto ATL

De forma predeterminada, el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md) genera nuevas clases con la macro ATL_NO_VTABLE, como se indica a continuación:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

A continuación, ATL define _ATL_NO_VTABLE como se indica a continuación:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

Si no define _ATL_DISABLE_NO_VTABLE, la macro ATL_NO_VTABLE se expande a `declspec(novtable)`. El `declspec(novtable)`uso de en una declaración de clase evita que el puntero vtable se inicialice en el constructor y el destructor de clase. Al compilar el proyecto, el vinculador elimina la tabla vtable y todas las funciones a las que apunta vtable.

Debe usar ATL_NO_VTABLE y, por consiguiente `declspec(novtable)`, solo con las clases base que no se pueden crear directamente. `declspec(novtable)` No debe utilizar con la clase más derivada del proyecto, ya que esta clase (normalmente [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md)o [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) inicializa el puntero vtable para el proyecto.

No debe llamar a funciones virtuales desde el constructor de cualquier objeto que use `declspec(novtable)`. Debe trasladar esas llamadas al método [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) .

Si no está seguro de si debe usar el `declspec(novtable)` modificador, puede quitar la macro ATL_NO_VTABLE de cualquier definición de clase o puede deshabilitarla globalmente especificando

```
#define _ATL_DISABLE_NO_VTABLE
```

en *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores), antes de que se incluyan todos los demás archivos de encabezado ATL.

## <a name="see-also"></a>Vea también

[Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Tipos de proyectos de C++ en Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)
