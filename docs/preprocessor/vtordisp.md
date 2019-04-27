---
title: vtordisp
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 67c6c329bcee75012f6075334760925eca945501
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179457"
---
# <a name="vtordisp"></a>vtordisp

**Específicos de C++**

Controla la adición del miembro oculto de desplazamiento de construcción/destrucción de vtordisp.

## <a name="syntax"></a>Sintaxis

```cpp
#pragma vtordisp([push,] n)
#pragma vtordisp(pop)
#pragma vtordisp()
#pragma vtordisp([push,] {on | off})
```

### <a name="parameters"></a>Parámetros

*push*<br/>
Inserta el valor actual de vtordisp en la pila interna del compilador y establece el nuevo valor de vtordisp en *n*.  Si *n* no se especifica, el valor actual de vtordisp no cambia.

*pop*<br/>
Quita el registro superior de la pila interna del compilador y restaura el valor vtordisp al valor quitado.

*n*<br/>
Especifica el nuevo valor de vtordisp. Los valores posibles son 0, 1 o 2, correspondiente a la `/vd0`, `/vd1`, y `/vd2` opciones del compilador. Para obtener más información, consulte [/vd (deshabilitar desplazamientos de constructores)](../build/reference/vd-disable-construction-displacements.md).

*on*<br/>
Equivalente a `#pragma vtordisp(1)`.

*off*<br/>
Equivalente a `#pragma vtordisp(0)`.

## <a name="remarks"></a>Comentarios

El **vtordisp** pragma solo es aplicable a código que usa bases virtuales. Si una clase derivada reemplaza una función virtual que hereda de una clase base virtual y, si un constructor o destructor para la clase derivada llama a esa función mediante un puntero a la clase base virtual, el compilador podría provocar ocultosadicionales**vtordisp** campos en clases con bases virtuales.

El **vtordisp** pragma afecta al diseño de clases que le siguen. El `/vd0`, `/vd1`, y `/vd2` opciones especifican el mismo comportamiento para módulos completos. Especificar 0 o *desactivar* suprime ocultar **vtordisp** miembros. Desactivar **vtordisp** solo si no hay ninguna posibilidad de que la clase constructores y destructores llaman a virtuales funciona en el objeto al que señala el **esto** puntero.

Especifica 1 o *en*, el valor predeterminado, que permite ocultar **vtordisp** miembros donde son necesarios.

Especificar 2 permite ocultar **vtordisp** miembros para todas las bases virtuales con funciones virtuales.  `vtordisp(2)` podría ser necesario para garantizar el funcionamiento correcto de **dynamic_cast** en un objeto parcialmente construido. Para obtener más información, consulte [advertencia del compilador (nivel 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`, sin argumentos, restaura el valor de vtordisp a la configuración inicial.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)