---
title: NCCALCSIZE_PARAMS (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07db612cb6dbde0dd762cf709ac6040bbd836c4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369728"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS (Estructura)
El `NCCALCSIZE_PARAMS` estructura contiene información que puede usar una aplicación mientras se procesaba la `WM_NCCALCSIZE` mensaje para calcular el tamaño, la posición y el contenido válido del área cliente de una ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *rgrc*  
 Especifica una matriz de rectángulos. La primera contiene las nuevas coordenadas de una ventana que se han movido o cambiar de tamaño. El segundo contiene las coordenadas de la ventana antes de se mueven o cambian de tamaño. La tercera contiene las coordenadas del área cliente de una ventana antes de se mueven o cambian de tamaño. Si la ventana es una ventana secundaria, las coordenadas son relativas al área del cliente de la ventana primaria. Si la ventana es una ventana de nivel superior, las coordenadas son relativas a la pantalla.  
  
 *lppos*  
 Apunta a un [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) estructura que contiene los valores de tamaño y la posición especificados en la operación que provocó la ventana para mover o cambiar de tamaño.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

