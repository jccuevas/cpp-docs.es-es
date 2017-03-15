---
title: Clase CD2DBrushProperties | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBrushProperties
- afxrendertarget/CD2DBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrushProperties class
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9f1a166950acda1f8341b58b82288d6f5cf9aeef
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dbrushproperties-class"></a>Clase CD2DBrushProperties
Contenedor para `D2D1_BRUSH_PROPERTIES`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Sobrecargado. Crea un `CD2D_BRUSH_PROPERTIES` (estructura)|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicializa el objeto|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_BRUSH_PROPERTIES`  
  
 `CD2DBrushProperties`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="a-namecd2dbrushpropertiesa--cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>CD2DBrushProperties::CD2DBrushProperties  
 Crea una estructura de CD2D_BRUSH_PROPERTIES  
  
```  
CD2DBrushProperties();  
CD2DBrushProperties(FLOAT _opacity);

 
CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,  
    FLOAT _opacity = 1.);
```  
  
### <a name="parameters"></a>Parámetros  
 `_opacity`  
 La base opacidad del pincel. El valor predeterminado es 1,0.  
  
 `_transform`  
 La transformación que se aplicará al pincel  
  
##  <a name="a-namecommoninita--cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrushProperties::CommonInit  
 Inicializa el objeto  
  
```  
void CommonInit();
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

