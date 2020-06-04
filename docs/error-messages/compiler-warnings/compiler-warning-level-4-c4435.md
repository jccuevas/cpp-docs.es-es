---
title: Advertencia del compilador (nivel 4) C4435
ms.date: 11/04/2016
f1_keywords:
- C4435
helpviewer_keywords:
- C4435
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 8021b6e4650a03b16c96711b8afe4f5fa57d2f07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185352"
---
# <a name="compiler-warning-level-4-c4435"></a>Advertencia del compilador (nivel 4) C4435

'clase1': La distribución de objetos de /vd2 cambiará debido a la base virtual 'clase2'

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

En la opción de compilación predeterminada de/VD1, la clase derivada no tiene un campo de `vtordisp` para la base virtual indicada.  Si/VD2 o `#pragma vtordisp(2)` está en vigor, se mostrará un campo `vtordisp`, cambiando el diseño del objeto.  Esto puede provocar problemas de compatibilidad binaria si los módulos interactivos se compilan con distintos valores de `vtordisp`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4435.

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>Consulte también

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (Deshabilitar desplazamientos de constructores)](../../build/reference/vd-disable-construction-displacements.md)
