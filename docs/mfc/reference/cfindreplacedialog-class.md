---
title: "CFindReplaceDialog Class | Microsoft Docs"
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
  - "CFindReplaceDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFindReplaceDialog class"
  - "Find/Replace dialog box"
  - "reemplazar texto"
  - "reemplazar texto, CFindReplaceDialog class"
  - "búsquedas de texto, CFindReplaceDialog class"
  - "búsquedas de texto, reemplazar texto"
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
caps.latest.revision: 25
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFindReplaceDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite implementar búsqueda de cadena estándar y reemplaza los cuadros de diálogo en la aplicación.  
  
## Sintaxis  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](../Topic/CFindReplaceDialog::CFindReplaceDialog.md)|Llame a esta función para construir un objeto de `CFindReplaceDialog` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](../Topic/CFindReplaceDialog::Create.md)|Crea y muestra un cuadro de diálogo de `CFindReplaceDialog` .|  
|[CFindReplaceDialog::FindNext](../Topic/CFindReplaceDialog::FindNext.md)|Llame a esta función para determinar si el usuario desea buscar la siguiente aparición de la cadena de búsqueda.|  
|[CFindReplaceDialog::GetFindString](../Topic/CFindReplaceDialog::GetFindString.md)|Llame a esta función para recuperar la cadena de búsqueda actual.|  
|[CFindReplaceDialog::GetNotifier](../Topic/CFindReplaceDialog::GetNotifier.md)|Llame a esta función para recuperar la estructura de **FINDREPLACE** en el controlador de mensajes registrado.|  
|[CFindReplaceDialog::GetReplaceString](../Topic/CFindReplaceDialog::GetReplaceString.md)|Llame a esta función para recuperar la actual reemplazan la cadena.|  
|[CFindReplaceDialog::IsTerminating](../Topic/CFindReplaceDialog::IsTerminating.md)|Llame a esta función para determinar si el cuadro de diálogo está finalizando.|  
|[CFindReplaceDialog::MatchCase](../Topic/CFindReplaceDialog::MatchCase.md)|Llame a esta función para determinar si el usuario desea coincidir con el caso de la cadena de búsqueda exactamente.|  
|[CFindReplaceDialog::MatchWholeWord](../Topic/CFindReplaceDialog::MatchWholeWord.md)|Llame a esta función para determinar si el usuario desea coincidir con palabras completas sólo.|  
|[CFindReplaceDialog::ReplaceAll](../Topic/CFindReplaceDialog::ReplaceAll.md)|Llame a esta función para determinar si el usuario desea todas las apariciones de la cadena que se va a reemplazar.|  
|[CFindReplaceDialog::ReplaceCurrent](../Topic/CFindReplaceDialog::ReplaceCurrent.md)|Llame a esta función para determinar si el usuario desea la palabra actual que se va a reemplazar.|  
|[CFindReplaceDialog::SearchDown](../Topic/CFindReplaceDialog::SearchDown.md)|Llame a esta función para determinar si el usuario desea búsqueda para continuar en una dirección abajo.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFindReplaceDialog::m\_fr](../Topic/CFindReplaceDialog::m_fr.md)|Una estructura utilizada para personalizar un objeto de `CFindReplaceDialog` .|  
  
## Comentarios  
 A diferencia de los otros cuadros de diálogo comunes de Windows, los objetos de `CFindReplaceDialog` son no modal, permitiendo a los usuarios interactuar con otras ventanas mientras están en la pantalla.  Hay dos tipos de objetos de `CFindReplaceDialog` : Los cuadros de diálogo de búsqueda y la búsqueda y reemplazar los cuadros de diálogo.  Aunque los cuadros de diálogo permiten al usuario entre búsqueda y búsqueda\/reemplaza cadenas, no realizan funciones que buscan o que reemplazan cualquiera de los.  Debe agregarlas a la aplicación.  
  
 Para construir un objeto de `CFindReplaceDialog` , utilice el constructor proporcionado \(que no tiene ningún argumento\).  Puesto que esto es un cuadro de diálogo no modal, asigne el objeto en el montón mediante el operador de **nuevo** , en lugar de en la pila.  
  
 Una vez que se ha construido un objeto de `CFindReplaceDialog` , se debe llamar a la función miembro de [cree](../Topic/CFindReplaceDialog::Create.md) para crear y mostrar el cuadro de diálogo.  
  
 Use la estructura de [m\_fr](../Topic/CFindReplaceDialog::m_fr.md) para inicializar el cuadro de diálogo antes de llamar a **Create**.  La estructura de `m_fr` es de [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)escrito.  Para obtener más información sobre esta estructura, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para que la ventana principal se notifique de búsqueda y reemplace las solicitudes, debe utilizar la función de Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) y utilizar la macro de mensaje\- mapa de [ON\_REGISTERED\_MESSAGE](../Topic/ON_REGISTERED_MESSAGE.md) en la ventana de marco que controle este mensaje registrado.  
  
 Puede determinar si el usuario ha decidido finalizar el cuadro de diálogo con la función miembro de `IsTerminating` .  
  
 `CFindReplaceDialog` se basa en el archivo de COMMDLG.DLL que envía con las versiones de Windows 3,1 y versiones posteriores.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CFindReplaceDialog`, proporcionar una plantilla personalizada del cuadro de diálogo, y agregar un mapa de mensajes para procesar mensajes de notificación de controles extendidos.  cualquier mensaje sin procesar se debe pasar a la clase base.  
  
 Personalizar la función de enlace no es necesario.  
  
 Para obtener más información sobre cómo utilizar `CFindReplaceDialog`, vea [Clases comunes de diálogo](../../mfc/common-dialog-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)