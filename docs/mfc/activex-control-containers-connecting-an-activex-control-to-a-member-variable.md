---
title: 'Contenedores de controles ActiveX: Conectar un Control ActiveX a una Variable de miembro | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a2b6a5ab17db7b512f1f44d2eda68169d71645
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333136"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro
La manera más fácil de obtener acceso a un control ActiveX desde dentro de su aplicación de contenedor de control es asociar el control ActiveX a una variable de miembro de la clase de cuadro de diálogo que contiene el control.  
  
> [!NOTE]
>  Esto no es la única manera de tener acceso a un control incrustado desde dentro de una clase de contenedor, pero para los fines de este artículo es suficiente.  
  
### <a name="adding-a-member-variable-to-the-dialog-class"></a>Agregar una variable miembro a la clase de cuadro de diálogo  
  
1.  Desde la vista de clases, haga clic en la clase de cuadro de diálogo principal para abrir el menú contextual. Por ejemplo: `CContainerDlg`.  
  
2.  En el menú contextual, haga clic en **agregar** y, a continuación, **agregar Variable**.  
  
3.  En el Asistente para agregar variables de miembro, haga clic en **la variable de Control**.  
  
4.  En el **Id. de Control** cuadro de lista, seleccione el identificador del control del control ActiveX incrustado. Por ejemplo: `IDC_CIRCCTRL1`.  
  
5.  En el **nombre de Variable** cuadro, escriba un nombre.  
  
     Por ejemplo: `m_circctl`.  
  
6.  Haga clic en **finalizar** para aceptar las opciones y salir del Asistente para agregar variables miembro.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

