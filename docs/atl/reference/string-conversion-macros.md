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
ms.openlocfilehash: 6a84424de81eba2e6ab1e1baf60f567ebf2739ee
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915508"
---
# <a name="string-conversion-macros"></a>Macros de conversión de cadenas

Estas macros proporcionan características de conversión de cadenas.

##  <a name="atl_and_mfc_string_conversion_macros"></a>Macros de conversión de cadenas de ATL y MFC

Las macros de conversión de cadena en las que se centra este tema son válidas tanto para ATL como para MFC. Para obtener más información sobre la conversión de cadenas [de MFC, vea TN059: Usar macros](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) de conversión MBCS/Unicode de MFC y [macros y variables globales de MFC](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>Macros de conversión de cadenas DEVMODE y TEXTMETRIC

Estas macros crean una copia de una estructura [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) o [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) y convierten las cadenas dentro de la nueva estructura en un nuevo tipo de cadena. Las macros asignan memoria en la pila para la nueva estructura y devuelven un puntero a la nueva estructura.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Comentarios

Por ejemplo:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

y:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

En los nombres de macro, el tipo de cadena de la estructura de origen está a la izquierda (por ejemplo, **a**) y el tipo de cadena de la estructura de destino está a la derecha (por ejemplo, **W**). **Un** representa LPSTR, **OLE** significa LPOLESTR, **T** significa LPTSTR y **W** representa a LPWStr.

Por lo tanto, DEVMODEA2W `DEVMODE` copia una estructura con cadenas LPSTR `DEVMODE` en una estructura con cadenas LPWStr, TEXTMETRICOLE2T `TEXTMETRIC` copia una estructura con cadenas LPOLESTR `TEXTMETRIC` en una estructura con cadenas LPTSTR, etc.

Las dos cadenas convertidas en `DEVMODE` la estructura son el nombre del`dmDeviceName`dispositivo () y el nombre`dmFormName`del formulario (). Las `DEVMODE` macros de conversión de cadenas también actualizan el`dmSize`tamaño de la estructura ().

Las cuatro cadenas convertidas en `TEXTMETRIC` la estructura son el primer carácter`tmFirstChar`(), el último carácter`tmLastChar`(), el carácter predeterminado`tmDefaultChar`() y el carácter de interrupción`tmBreakChar`().

El comportamiento de las `DEVMODE` macros de conversión de cadena y `TEXTMETRIC` depende de la Directiva del compilador en vigor, si existe. Si los tipos de origen y de destino son el mismo, no tiene lugar ninguna conversión. Las directivas de compilador cambian **T** y **OLE** como se indica a continuación:

|Directiva de compilador vigente|T pasa a|OLE pasa a|
|----------------------------------|---------------|-----------------|
|ninguna|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|Unicode y **OLE2ANSI**  **\_**|**W**|**A**|

En la tabla siguiente se `DEVMODE` enumeran las macros de conversión de cadenas y `TEXTMETRIC` .

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
