---
title: "Macros de conversión de cadena | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 89790d1a56f64e6479ae32d72c529142ba8df1de
ms.openlocfilehash: 0dce243b0f7db087db908d603e6cd1cfc4b02db8
ms.lasthandoff: 02/24/2017

---
# <a name="string-conversion-macros"></a>Macros de conversión de cadenas
Estas macros proporcionan funciones de conversión de cadena.  
  
|||  
|-|-|  
|[Macros de conversión de cadenas MFC y ATL](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)|Conjunto de macros de conversión entre tipos de cadena.|  
|[DEVMODE y Macros de conversión de cadena TEXTMETRIC](http://msdn.microsoft.com/library/85cebec0-2a18-48e5-9c1c-99d5b7f15425)|Conjunto de macros que convertir las cadenas en `DEVMODE` y `TEXTMETRIC` estructuras.|  
  
##  <a name="a-nameatlandmfcstringconversionmacrosa--atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>Macros de conversión de cadenas MFC y ATL  
 Las macros de conversión de cadena en las que se centra este tema son válidas tanto para ATL como para MFC. Para obtener más información sobre la conversión de cadena MFC, vea [TN059: usar Macros de conversión de MBCS/Unicode de MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) y [MFC Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md).  
  
##  <a name="a-namedevmodeandtextmetricstringconversionmacrosa--devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE y Macros de conversión de cadena TEXTMETRIC  
 Estas macros crean una copia de un [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) o [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructurar y convertir las cadenas dentro de la estructura nuevo a un nuevo tipo de cadena. Las macros de asignación memoria en la pila de la nueva estructura y devuelven un puntero a la nueva estructura.  
  
```
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Utilities&#128;](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
 y:  
  
 [!code-cpp[NVC_ATL_Utilities&#129;](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
 En los nombres de macro, el tipo de cadena en la estructura de origen está a la izquierda (por ejemplo, **A**) y el tipo de cadena en la estructura de destino está a la derecha (por ejemplo, **W**). **A** stands for **LPSTR**, **OLE** stands for `LPOLESTR`, **T** stands for `LPTSTR`, and **W** stands for `LPWSTR`.  
  
 Por lo tanto, `DEVMODEA2W` copias un `DEVMODE` estructura con **LPSTR** cadenas en una `DEVMODE` estructura con `LPWSTR` cadenas, `TEXTMETRICOLE2T` copias un `TEXTMETRIC` estructura con `LPOLESTR` cadenas en una `TEXTMETRIC` estructura con `LPTSTR` cadenas y así sucesivamente.  
  
 Las dos cadenas se convierten en el `DEVMODE` estructura son el nombre de dispositivo ( **dmDeviceName**) y el nombre del formulario ( **dmFormName**). El `DEVMODE` macros de conversión de cadena también actualización el tamaño de la estructura ( **dmSize**).  
  
 Las cuatro cadenas de convertir en el `TEXTMETRIC` estructura son el primer carácter ( **tmFirstChar**), el último carácter ( **tmLastChar**), el carácter predeterminado ( **tmDefaultChar**) y el carácter de salto ( **tmBreakChar**).  
  
 El comportamiento de la `DEVMODE` y `TEXTMETRIC` macros de conversión de cadenas depende de la directiva de compilador vigente, si existe. Si los tipos de origen y de destino son el mismo, no tiene lugar ninguna conversión. Cambian las directivas de compilador **T** y **OLE** como sigue:  
  
|Directiva de compilador vigente|T pasa a|OLE pasa a|  
|----------------------------------|---------------|-----------------|  
|ninguna|**A**|**W**|  
|**_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**_UNICODE** y **OLE2ANSI**|**W**|**A**|  
  
 La siguiente tabla se enumeran los `DEVMODE` y `TEXTMETRIC` macros de conversión de cadena.  
  
### <a name="devmode-and-textmetric-string-conversion-macros"></a>DEVMODE y Macros de conversión de cadena TEXTMETRIC  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)


