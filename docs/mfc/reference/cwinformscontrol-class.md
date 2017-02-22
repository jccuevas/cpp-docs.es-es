---
title: "CWinFormsControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsControl class"
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CWinFormsControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad básica para hospedar un control de formularios Windows Forms.  
  
## Sintaxis  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### Parámetros  
 `TManagedControl`  
 Un control de formularios Windows Forms de .NET Framework que se mostrará en la aplicación MFC.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsControl::CWinFormsControl](../Topic/CWinFormsControl::CWinFormsControl.md)|Construye un objeto contenedor de control de Windows Forms de MFC.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md)|Crea un control de formularios Windows Forms en un contenedor MFC.|  
|[CWinFormsControl::GetControl](../Topic/CWinFormsControl::GetControl.md)|Recupera un puntero al control de Windows Forms.|  
|[CWinFormsControl::GetControlHandle](../Topic/CWinFormsControl::GetControlHandle.md)|Recupera un identificador al control de Windows Forms.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsControl::operator \-\>](../Topic/CWinFormsControl::operator%20-%3E.md)|reemplaza [CWinFormsControl::GetControl](../Topic/CWinFormsControl::GetControl.md) en expresiones.|  
|[CWinFormsControl::operator TManagedControl^](../Topic/CWinFormsControl::operator%20TManagedControl%5E.md)|Convierte un tipo como un puntero a un control de formularios Windows Forms.|  
  
## Comentarios  
 La clase de `CWinFormsControl` proporciona funcionalidad básica para hospedar un control de formularios Windows Forms.  
  
 Para obtener más información sobre cómo utilizar los formularios Windows Forms, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 El código MFC no debe almacenar en caché los identificadores de ventana \(almacenados normalmente en `m_hWnd`\).  Las propiedades del control de Windows Forms requieren que Win32 subyacente `Window` se destruirá y crear mediante `DestroyWindow` y `CreateWindow`.  La aplicación de Windows Forms de MFC controla los eventos de `Destroy` y de `Create` de controles para actualizar el miembro de `m_hWnd` .  
  
> [!NOTE]
>  La integración de formularios Windows Forms de MFC sólo funciona en proyectos que se vinculen dinámicamente a MFC \(en qué AFXDLL es definido\).  
  
## Requisitos  
 **encabezado:** afxwinforms.h  
  
## Vea también  
 [CWinFormsDialog Class](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)