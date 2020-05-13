---
title: Macros de conversión de cadenas
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: 8df496b78334d26e7d3664642b2e9d93d6149843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325854"
---
# <a name="string-conversion-macros"></a>Macros de conversión de cadenas

Estas macros proporcionan características de conversión de cadenas.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>Macros de conversión de cadenas ATL y MFC

Las macros de conversión de cadena en las que se centra este tema son válidas tanto para ATL como para MFC. Para obtener más información sobre la conversión de cadenas MFC, vea [TN059: Uso de macros de conversión MBCS/Unicode](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) de MFC y [macros y valores globales de MFC](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>Macros de conversión de cadenas DEVMODE y TEXTMETRIC

Estas macros crean una copia de una estructura [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) o [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) y convierten las cadenas dentro de la nueva estructura en un nuevo tipo de cadena. Las macros asignan memoria en la pila para la nueva estructura y devuelven un puntero a la nueva estructura.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Observaciones

Por ejemplo:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

y:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

En los nombres de macro, el tipo de cadena de la estructura de origen está a la izquierda (por ejemplo, **A**) y el tipo de cadena de la estructura de destino está a la derecha (por ejemplo, **W**). **A** significa LPSTR, **OLE** significa LPOLESTR, **T** significa LPTSTR y **W** significa LPWSTR.

Por lo tanto, DEVMODEA2W `DEVMODE` copia una `DEVMODE` estructura con cadenas LPSTR en una estructura `TEXTMETRIC` con cadenas LPWSTR, TEXTMETRICOLE2T copia una estructura con cadenas LPOLESTR en una `TEXTMETRIC` estructura con cadenas LPTSTR, etc.

Las dos cadenas `DEVMODE` convertidas en`dmDeviceName`la estructura son`dmFormName`el nombre del dispositivo ( ) y el nombre del formulario ( ). Las `DEVMODE` macros de conversión de`dmSize`cadenas también actualizan el tamaño de la estructura ( ).

Las cuatro cadenas `TEXTMETRIC` convertidas en`tmFirstChar`la estructura son`tmLastChar`el primer`tmDefaultChar`carácter ( ),`tmBreakChar`el último carácter ( ), el carácter predeterminado ( ) y el carácter de interrupción ( ).

El comportamiento `DEVMODE` de `TEXTMETRIC` las macros de conversión de cadenas y depende de la directiva del compilador en vigor, si existe. Si los tipos de origen y de destino son el mismo, no tiene lugar ninguna conversión. Las directivas del compilador cambian **T** y **OLE de** la siguiente manera:

|Directiva de compilador vigente|T pasa a|OLE pasa a|
|----------------------------------|---------------|-----------------|
|None|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE y **OLE2ANSI** ** \_**|**W**|**A**|

En la tabla `DEVMODE` `TEXTMETRIC` siguiente se enumeran las macros de conversión de cadenas y y.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
