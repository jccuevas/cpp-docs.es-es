---
title: NCCALCSIZE_PARAMS (estructura) | Microsoft Docs
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
ms.openlocfilehash: 095b66af9dab08e3d8fad040c43e2eaf8d2beb81
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335648"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS (Estructura)
El `NCCALCSIZE_PARAMS` estructura contiene información que puede usar una aplicación al procesar el mensaje WM_NCCALCSIZE para calcular el tamaño, posición y contenido válido del área cliente de una ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *rgrc*  
 Especifica una matriz de rectángulos. El primero contiene las nuevas coordenadas de una ventana que se han movido o cambiar de tamaño. El segundo contiene las coordenadas de la ventana antes de que se mueve o cambia de tamaño. La tercera contiene las coordenadas del área cliente de una ventana antes de que se mueve o cambia de tamaño. Si la ventana es una ventana secundaria, las coordenadas son en relación con el área cliente de la ventana primaria. Si la ventana es una ventana de nivel superior, las coordenadas son relativas a la pantalla.  
  
 *lppos*  
 Apunta a un [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) estructura que contiene los valores de tamaño y la posición especificados en la operación que provocó la ventana se deben mover o cambiar de tamaño.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

