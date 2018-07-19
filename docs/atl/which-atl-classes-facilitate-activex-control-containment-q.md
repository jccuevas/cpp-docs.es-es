---
title: ¿Qué clases ATL facilitan la contención de controles ActiveX? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f024e9929e916e15b110bfc32bc704c4aef755a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361962"
---
# <a name="which-atl-classes-facilitate-activex-control-containment"></a>¿Qué clases ATL facilitan la contención de controles ActiveX?
El código de hospedaje de controles de ATL no requiere que se va a utilizar ninguna clase ATL; puede crear simplemente una **"AtlAxWin80"** ventana y use la API de hospedaje de controles si es necesario (para obtener más información, consulte **¿qué es la API de hospedaje de controles de ATL**. Sin embargo, las clases siguientes hacen que las características de contención más fácil de usar.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|Ajusta un **"AtlAxWin80"** ventana, que proporciona métodos para crear la ventana, crear un control o adjuntar un control a la ventana y recuperar punteros de interfaz en el objeto host.|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Ajusta un **"AtlAxWinLic80"** ventana, que proporciona métodos para crear la ventana, crear un control o adjuntar un control con licencia a la ventana y recuperar punteros de interfaz en el objeto host.|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Actúa como clase base para clases de controles ActiveX en función de un recurso de cuadro de diálogo. Estos controles pueden contener otros controles ActiveX.|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Actúa como clase base para clases de cuadro de diálogo basadas en un recurso de cuadro de diálogo. Estos controles pueden contener controles ActiveX.|  
|[CWindow](../atl/reference/cwindow-class.md)|Proporciona un método, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), que devuelve un puntero de interfaz en un control, dado el identificador de su ventana host. Además, los contenedores de la API de Windows exponen por `CWindow` suele facilitar la administración de ventanas.|  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

