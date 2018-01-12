---
title: "Macros de conversión de cadena | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0a166fec6eceb84b1b22563849ff1b9462ef9a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="string-conversion-macros"></a>Macros de conversión de cadenas

Estas macros proporcionan funciones de conversión de cadena.  
 
##  <a name="atl_and_mfc_string_conversion_macros"></a>Macros de conversión de cadena MFC y ATL

Las macros de conversión de cadena en las que se centra este tema son válidas tanto para ATL como para MFC. Para obtener más información sobre la conversión de cadenas MFC, vea [TN059: usar Macros de conversión de MBCS/Unicode de MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) y [globales y Macros de MFC](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>Macros de conversión de cadenas TEXTMETRIC y DEVMODE

Estas macros crean una copia de un [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) o [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) permite organizar y convertir las cadenas dentro de la nueva estructura a un nuevo tipo de cadena. Las macros de asignación memoria en la pila para la nueva estructura y devuelven un puntero a la nueva estructura.  
  
```cpp
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>Comentarios

Por ejemplo:  
  
[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
y:  
  
[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
Los nombres de macro, el tipo de cadena en la estructura de origen está a la izquierda (por ejemplo, **A**) y el tipo de cadena en la estructura de destino está a la derecha (por ejemplo, **W**). **A** es el acrónimo `LPSTR`, **OLE** es el acrónimo `LPOLESTR`, **T** es el acrónimo `LPTSTR`, y **W** representa `LPWSTR`.  
  
Por lo tanto, **DEVMODEA2W** copias un `DEVMODE` estructura con `LPSTR` cadenas en una `DEVMODE` estructura con `LPWSTR` cadenas, **TEXTMETRICOLE2T** copia una `TEXTMETRIC`estructura con `LPOLESTR` cadenas en una `TEXTMETRIC` estructura con `LPTSTR` cadenas y así sucesivamente.  
  
Las dos cadenas que se convierte en el `DEVMODE` estructura son el nombre de dispositivo (`dmDeviceName`) y el nombre del formulario (`dmFormName`). El `DEVMODE` macros de conversión de cadena actualización también el tamaño de la estructura (`dmSize`).  
  
Las cuatro cadenas convertidas en el `TEXTMETRIC` estructura son el primer carácter (`tmFirstChar`), el último carácter (`tmLastChar`), el carácter predeterminado (`tmDefaultChar`) y el carácter de salto (`tmBreakChar`).
  
El comportamiento de la `DEVMODE` y `TEXTMETRIC` macros de conversión de cadenas depende de la directiva de compilador vigente, si existe. Si los tipos de origen y de destino son el mismo, no tiene lugar ninguna conversión. Cambian las directivas de compilador **T** y **OLE** como se indica a continuación:  
  
|Directiva de compilador vigente|T pasa a|OLE pasa a|  
|----------------------------------|---------------|-----------------|  
|ninguna|**A**|**W**|  
|**\_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**\_UNICODE** y **OLE2ANSI**|**W**|**A**|  
  
 La siguiente tabla se recogen los `DEVMODE` y `TEXTMETRIC` macros de conversión de cadena.  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
