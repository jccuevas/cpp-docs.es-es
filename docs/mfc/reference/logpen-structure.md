---
title: LOGPEN (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f3868d2ac6a7b18cfe43f7da8865aed0a3ecf88d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="logpen-structure"></a>LOGPEN (Estructura)
El `LOGPEN` estructura define el estilo, ancho y color de un lápiz, un objeto de dibujo que se utiliza para dibujar líneas y bordes. El [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) función utiliza la `LOGPEN` estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *lopnStyle*  
 Especifica el tipo de lápiz. Este miembro puede ser uno de los siguientes valores:  
  
- **PS_SOLID** crea un lápiz sólido.  
  
- **PS_DASH** crea un lápiz rayado. (Válido sólo si el ancho del lápiz es 1).  
  
- **PS_DOT** crea un lápiz con puntos. (Válido sólo si el ancho del lápiz es 1).  
  
- **PS_DASHDOT** crea un lápiz con guiones y puntos alternativamente. (Válido sólo si el ancho del lápiz es 1).  
  
- **PS_DASHDOTDOT** crea un lápiz con guiones y puntos dobles alternos. (Válido sólo si el ancho del lápiz es 1).  
  
- **PS_NULL** crea un lápiz null.  
  
- **PS_INSIDEFRAME** crea un lápiz que dibuja una línea dentro del marco de las formas cerradas generados por funciones de salida GDI que especifican un rectángulo delimitador (por ejemplo, el **elipse**, **rectángulo**, `RoundRect`, `Pie`, y `Chord` funciones miembro). Cuando se utiliza este estilo con GDI funciones que no se especifican un rectángulo delimitador de salida (por ejemplo, el `LineTo` función miembro), el área de dibujo del lápiz no está limitado por un marco.  
  
     Si tiene un lápiz la **PS_INSIDEFRAME** estilo y un color que no coincide con un color en la tabla de colores lógica, se dibuja el lápiz con un color interpolado. El **PS_SOLID** no se puede usar el estilo de pluma para crear un lápiz con un color interpolado. El **PS_INSIDEFRAME** estilo es idéntico a **PS_SOLID** si el ancho del lápiz es menor o igual que 1.  
  
     Cuando el **PS_INSIDEFRAME** estilo se usa con objetos GDI producidos por las funciones que no sea **elipse**, **rectángulo**, y `RoundRect`, la línea no puede estar completamente dentro del marco especificado.  
  
 *lopnWidth*  
 Especifica el ancho del lápiz, en unidades lógicas. Si el **lopnWidth** miembro es 0, el lápiz es 1 píxel de ancho en dispositivos de trama independientemente del modo de asignación actual.  
  
 *lopnColor*  
 Especifica el color del lápiz.  
  
## <a name="remarks"></a>Comentarios  
 El **y** valor en el [punto](../../mfc/reference/point-structure1.md) estructura para el **lopnWidth** miembro no se usa.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)


