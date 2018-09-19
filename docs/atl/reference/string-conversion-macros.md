---
title: Macros de conversión de cadena | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4df562e693a412ca93720748f929d1bbcefc829
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760466"
---
# <a name="string-conversion-macros"></a>Macros de conversión de cadena

Estas macros proporcionan funciones de conversión de cadena.  

##  <a name="atl_and_mfc_string_conversion_macros"></a>  Macros de conversión de cadena MFC y ATL

Las macros de conversión de cadena en las que se centra este tema son válidas tanto para ATL como para MFC. Para obtener más información sobre la conversión de cadenas MFC, vea [TN059: usar Macros de conversión de MBCS/Unicode de MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) y [globales y Macros de MFC](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  Macros de conversión de cadenas TEXTMETRIC y DEVMODE

Estas macros crean una copia de un [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) o [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) estructurar y convertir las cadenas dentro de la nueva estructura a un nuevo tipo de cadena. Las macros de asignación memoria en la pila para la nueva estructura y devuelven un puntero a la nueva estructura.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Comentarios

Por ejemplo:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

y:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

Los nombres de macro, el tipo de cadena en la estructura de origen está a la izquierda (por ejemplo, **A**) y el tipo de cadena en la estructura de destino está a la derecha (por ejemplo, **W**). **Un** LPSTR, es el acrónimo **OLE** LPOLESTR, es el acrónimo **T** LPTSTR, es el acrónimo y **W** significa LPWSTR.

Por lo tanto, se copia DEVMODEA2W un `DEVMODE` estructura con LPSTR cadenas en un `DEVMODE` estructura con cadenas LPWSTR, TEXTMETRICOLE2T copias un `TEXTMETRIC` estructura con LPOLESTR cadenas en un `TEXTMETRIC` estructura con cadenas LPTSTR y así sucesivamente.

Las dos cadenas se convierten en el `DEVMODE` estructura son el nombre del dispositivo (`dmDeviceName`) y el nombre del formulario (`dmFormName`). El `DEVMODE` macros de conversión de cadena también actualización el tamaño de la estructura (`dmSize`).

Las cuatro cadenas convertidas en el `TEXTMETRIC` estructura son el primer carácter (`tmFirstChar`), el último carácter (`tmLastChar`), el carácter predeterminado (`tmDefaultChar`) y el carácter de salto (`tmBreakChar`).

El comportamiento de la `DEVMODE` y `TEXTMETRIC` macros de conversión de cadenas depende de la directiva de compilador en efecto, si existe. Si los tipos de origen y de destino son el mismo, no tiene lugar ninguna conversión. Cambiar las directivas de compilador **T** y **OLE** como sigue:

|Directiva de compilador vigente|T pasa a|OLE pasa a|
|----------------------------------|---------------|-----------------|
|ninguna|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|**\_UNICODE** y **OLE2ANSI**|**W**|**A**|

La siguiente tabla se enumeran los `DEVMODE` y `TEXTMETRIC` macros de conversión de cadena.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|  

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
