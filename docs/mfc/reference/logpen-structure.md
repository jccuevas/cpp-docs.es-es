---
title: LOGPEN (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c0e07ce3a38eaca54e860ebe821924c0f564c69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374155"
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
  
- **PS_DASH** crea un lápiz discontinuo. (Válido únicamente si el ancho del lápiz es 1).  
  
- **PS_DOT** crea un lápiz con puntos. (Válido únicamente si el ancho del lápiz es 1).  
  
- **PS_DASHDOT** crea un lápiz con guiones y puntos alternativamente. (Válido únicamente si el ancho del lápiz es 1).  
  
- **PS_DASHDOTDOT** crea un lápiz con guiones y puntos dobles alternos. (Válido únicamente si el ancho del lápiz es 1).  
  
- **PS_NULL** crea un lápiz null.  
  
- **PS_INSIDEFRAME** crea un lápiz que dibuja una línea dentro del marco de las formas cerradas generados por funciones de salida GDI que especifican un rectángulo delimitador (por ejemplo, el **elipse**, **rectángulo**, `RoundRect`, `Pie`, y `Chord` funciones miembro). Cuando se utiliza este estilo con GDI funciones que no especifican un rectángulo delimitador de salida (por ejemplo, el `LineTo` función miembro), el área de dibujo del lápiz no está limitado por un marco.  
  
     Si tiene un lápiz el **PS_INSIDEFRAME** estilo y un color que no coincide con un color en la tabla de colores lógica, se dibuja el lápiz con un color interpolado. El **PS_SOLID** estilo del lápiz no se puede usar para crear un lápiz con un color interpolado. El **PS_INSIDEFRAME** estilo es idéntico a **PS_SOLID** si el ancho del lápiz es menor o igual que 1.  
  
     Cuando el **PS_INSIDEFRAME** estilo se utiliza con objetos GDI generados por funciones excepto **elipse**, **rectángulo**, y `RoundRect`, la línea no puede ser totalmente dentro del marco especificado.  
  
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

