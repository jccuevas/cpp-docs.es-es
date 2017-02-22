---
title: "Acceso con seguridad de tipos a los controles con Asistentes para c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para código"
  - "DDX (intercambio de datos de cuadros de diálogo), obtener acceso a controles"
  - "controles de cuadro de diálogo, obtener acceso"
  - "cuadros de diálogo, obtener acceso a controles"
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Acceso con seguridad de tipos a los controles con Asistentes para c&#243;digo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si está familiarizado con las características de DDX, puede utilizar la propiedad del Control en [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para crear el acceso tipo\- seguro.  Este enfoque es más fácil que crear controles sin los asistentes para código.  
  
 Si desea simplemente el acceso al valor de un control, DDX lo proporciona.  Si desea algo más que el valor de un control, utilice el asistente para agregar variables miembro para agregar una variable miembro de la clase correspondiente a la clase de diálogo.  Adjunte a esta variable miembro a la propiedad del Control.  
  
 Las variables miembro puede tener una propiedad de Control en lugar de una propiedad Value.  La propiedad Value hace referencia al tipo de datos devueltos del control, como `CString` o `int`.  La propiedad del Control habilita el acceso directo al control a través de un miembro de datos cuyo tipo es una de las clases control en MFC, como `CButton` o `CEdit`.  
  
> [!NOTE]
>  Para un control, se especificados puede, si deseo, tener variables miembro varias con la propiedad Value y a lo sumo una variable miembro con la propiedad del Control.  Sólo se puede hacer un objeto MFC asignarlo a un control porque varios objetos asociados a un control, o cualquier otra ventana, conducirían a una ambigüedad en el mapa de mensajes.  
  
 Puede utilizar este objeto para llamar a la función miembro para el objeto de control.  Tales llamadas afectan al control en el cuadro de diálogo.  Por ejemplo, para un control checkbox representado por `m_Checkbox`variable, de `CButton`escrito, podría llamar a:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/CPP/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 Aquí la variable miembro `m_Checkbox` responde al mismo propósito que la función `GetMyCheckbox` miembro mostrado en [Tipo \- y Acceso a los asistentes para código de Sin controls](../mfc/type-safe-access-to-controls-without-code-wizards.md).  Si la casilla no es una casilla auto, todavía necesitaría un controlador en la clase de diálogo para el mensaje de la CONTROL\- notificación de **BN\_CLICKED** cuando se hace clic en el botón.  
  
 Para obtener más información sobre controles, vea [Controles](../mfc/controls-mfc.md).  
  
## Vea también  
 [Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Acceso con seguridad de tipos a los controles sin Asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)