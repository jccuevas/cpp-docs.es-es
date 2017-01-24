---
title: "CWndClassInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWndClassInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWndClassInfo class"
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWndClassInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para registrar información para una clase de ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CWndClassInfo  
  
```  
  
## Members  
  
### Métodos públicos  
  
|||  
|-|-|  
|[Register](../Topic/CWndClassInfo::Register.md)|registrar la clase de ventana.|  
  
### miembros de datos  
  
|||  
|-|-|  
|[m\_atom](../Topic/CWndClassInfo::m_atom.md)|Identifica la clase de ventana registrada.|  
|[m\_bSystemCursor](../Topic/CWndClassInfo::m_bSystemCursor.md)|Especifica si el recurso de cursor hace referencia a un sistema cursor o cursor contenido en un recurso de módulo.|  
|[m\_lpszCursorID](../Topic/CWndClassInfo::m_lpszCursorID.md)|Especifica el nombre de recurso del cursor.|  
|[m\_lpszOrigName](../Topic/CWndClassInfo::m_lpszOrigName.md)|contiene el nombre de una clase de ventana existente.|  
|[m\_szAutoName](../Topic/CWndClassInfo::m_szAutoName.md)|Contiene un nombre ATL\-generado de la clase de ventana.|  
|[m\_wc](../Topic/CWndClassInfo::m_wc.md)|mantiene la información de la clase de ventana en una estructura de **WNDCLASSEX** .|  
|[pWndProc](../Topic/CWndClassInfo::pWndProc.md)|Puntos al procedimiento de ventana de una clase de ventana existente.|  
  
## Comentarios  
 `CWndClassInfo` administra la información de una clase de ventana.  Normalmente se utiliza `CWndClassInfo` con uno de tres macros, `DECLARE_WND_CLASS`, `DECLARE_WND_CLASS_EX`, o `DECLARE_WND_SUPERCLASS`, como se describe en la tabla siguiente:  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md)|información de los registros de`CWndClassInfo` para una nueva clase de ventana.|  
|[DECLARE\_WND\_CLASS\_EX](../Topic/DECLARE_WND_CLASS_EX.md)|`CWndClassInfo` registra información para una nueva clase de ventana, incluidos los parámetros de clase.|  
|[DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md)|`CWndClassInfo` registra información para una clase de ventana que se base en una clase existente pero use otro procedimiento de ventana.  Se llama a esta técnica el crear superclase.|  
  
 de forma predeterminada, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) incluye la macro de `DECLARE_WND_CLASS` para crear una ventana basada en una nueva clase de ventana.  DECLARE\_WND\_CLASS proporciona estilos predeterminados y el color de fondo del control.  Si desea especificar el estilo y el color de fondo personalmente, derive la clase de `CWindowImpl` e incluya la macro de `DECLARE_WND_CLASS_EX` en la definición de clase.  
  
 Si desea crear una ventana basada en una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro de `DECLARE_WND_SUPERCLASS` en la definición de clase.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/CPP/cwndclassinfo-class_1.h)]  
  
 Para obtener más información sobre las clases de ventana, vea [clases de ventana](http://msdn.microsoft.com/library/windows/desktop/ms632596) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre cómo utilizar las ventanas en ATL, vea el artículo [Clases de ventana ATL](../../atl/atl-window-classes.md).  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)