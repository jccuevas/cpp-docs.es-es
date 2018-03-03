---
title: Clase COleControlModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OleControlModule
dev_langs:
- C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 196b69a0d86c3809415e030adb567c8642051f40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="colecontrolmodule-class"></a>Clase COleControlModule
La clase base de la que se deriva un objeto de módulo de control OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones miembro para inicializar el módulo de control. Cada módulo de control OLE que utiliza Microsoft Foundation classes solo puede contener un objeto derivado de `COleControlModule`. Este objeto se crea cuando se crean otros objetos globales de C++. Declarar la derivada `COleControlModule` objeto en el nivel global.  
  
 Para obtener más información sobre el uso de la `COleControlModule` de clases, consulte la [CWinApp](../../mfc/reference/cwinapp-class.md) clase y el artículo [controles ActiveX](../../mfc/mfc-activex-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC TESTHELP](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



