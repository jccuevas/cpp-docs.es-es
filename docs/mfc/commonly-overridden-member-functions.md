---
title: "Funciones miembro que se reemplazan con frecuencia | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialog (clase), miembros"
  - "clases de cuadro de diálogo, funciones miembro que se reemplazan con frecuencia"
  - "cuadros de diálogo de MFC, reemplazar funciones miembro"
  - "OnCancel (función)"
  - "OnInitDialog (función)"
  - "OnOK (función)"
  - "reemplazar, miembros de clases del cuadro de diálogo"
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones miembro que se reemplazan con frecuencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente se enumeran las funciones más probable miembro reemplazar en `CDialog`\- clase derivada.  
  
### Funciones normalmente invalidadas miembro de clase CDialog  
  
|Función miembro|Mensaje responde a|Propósito de reemplazo|  
|---------------------|------------------------|----------------------------|  
|`OnInitDialog`|**WM\_INITDIALOG**|Inicializa los controles del cuadro de diálogo.|  
|`OnOK`|**BN\_CLICKED** para el botón **IDOK**|Responder cuando el usuario hace clic en el botón ACEPTAR.|  
|`OnCancel`|**BN\_CLICKED** para el botón **IDCANCEL**|Responder cuando el usuario hace clic en el botón cancel.|  
  
 `OnInitDialog`, `OnOK`, y `OnCancel` son funciones virtuales.  Para reemplazar, declare una función de reemplazo de la clase derivada de diálogo mediante [Ventana Propiedades](../Topic/Properties%20Window.md).  
  
 se llama`OnInitDialog` justo antes de que se muestra el cuadro de diálogo.  Debe llamar al controlador predeterminado de `OnInitDialog` de reemplazo — normalmente como la primera acción del controlador.  De forma predeterminada, `OnInitDialog` devuelve **VERDADERO** para indicar que el foco se debe establecer en el primer control en el cuadro de diálogo.  
  
 `OnOK` se invalida normalmente para cuadros de diálogo no modales y no modales.  Si se invalida este controlador para un cuadro de diálogo modal, llame a la versión de la clase base de reemplazo — asegurarse que `EndDialog` se llama — o la llamada `EndDialog` personalmente.  
  
 `OnCancel` se invalida normalmente para los cuadros de diálogo no modal.  
  
 Para obtener más información sobre estas funciones miembro, vea la clase [CDialog](../mfc/reference/cdialog-class.md) en *la referencia de MFC* y explicación en [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md).  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Funciones miembro que se agregan con frecuencia](../mfc/commonly-added-member-functions.md)