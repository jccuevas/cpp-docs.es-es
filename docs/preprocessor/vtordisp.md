---
title: tvtordisp (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 3c676ab2bfee1b6cf3caff3ab456a4f23f2744c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216484"
---
# <a name="vtordisp-pragma"></a>tvtordisp (Pragma)

**C++Cuestión**

Controla la adición del miembro oculto `vtordisp` de desplazamiento de construcción o destrucción.

## <a name="syntax"></a>Sintaxis

> **#pragma vtordisp (** [ **Inserte,** ] *n* **)** \
> **#pragma vtordisp (pop)** \
> **#pragma vtordisp ()** \
> **#pragma vtordisp (** [ **inserciones,** ] { **on** | **OFF** } **)**

### <a name="parameters"></a>Parámetros

**enviar**\
Envía la configuración actual `vtordisp` en la pila interna del compilador y establece la `vtordisp` nueva configuración en *n*.  Si no se especifica *n* , la `vtordisp` configuración actual no cambia.

**emergente**\
Quita el registro superior de la pila interna del compilador y restaura la `vtordisp` configuración en el valor que se ha quitado.

*n*\
Especifica el nuevo valor para la `vtordisp` configuración. Los valores posibles son 0, 1 o 2, correspondientes a `/vd0`las `/vd1`opciones del `/vd2` compilador, y. Para obtener más información, vea [/Vd (deshabilitar desplazamientos de construcción)](../build/reference/vd-disable-construction-displacements.md).

**en**\
Equivalente a `#pragma vtordisp(1)`.

**habilitar**\
Equivalente a `#pragma vtordisp(0)`.

## <a name="remarks"></a>Comentarios

La Directiva pragma **vtordisp** solo es aplicable al código que usa bases virtuales. Si una clase derivada reemplaza una función virtual que hereda de una clase base virtual y si un constructor o destructor para la clase derivada llama a esa función con un puntero a la clase base virtual, el compilador puede incluir campos ocultos adicionales de `vtordisp` en clases con bases virtuales.

La Directiva pragma **vtordisp** afecta al diseño de las clases que la siguen. Las `/vd0`opciones `/vd1`, y`/vd2` especifican el mismo comportamiento para los módulos completos. Si se especifica 0 o **OFF** , se suprimen los miembros ocultos `vtordisp` . Desactive **vtordisp** solo si no hay ninguna posibilidad de que los constructores y destructores de la clase llamen a funciones virtuales en el objeto al `this` que apunta el puntero.

Si se especifica 1 o **en**, el valor predeterminado, se `vtordisp` habilitan los miembros ocultos en los que son necesarios.

Si se especifica 2, se `vtordisp` habilitan los miembros ocultos para todas las bases virtuales con funciones virtuales.  `#pragma vtordisp(2)`podría ser necesario para garantizar el rendimiento correcto de **dynamic_cast** en un objeto construido parcialmente. Para obtener más información, vea [Advertencia del compilador (nivel 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`, sin argumentos, restaura la `vtordisp` configuración a su valor inicial.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
