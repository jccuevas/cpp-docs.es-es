---
title: "CDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialog class"
  - "cuadros de diálogo de MFC, clase base"
  - "cuadros de diálogo modales, crear"
  - "cuadros de diálogo no modales, crear"
  - "cuadros de diálogo no modales, mostrar"
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base utilizada para mostrar cuadros de diálogo en la pantalla.  
  
## Sintaxis  
  
```  
class CDialog : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialog::CDialog](../Topic/CDialog::CDialog.md)|Crea un objeto `CDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialog::Create](../Topic/CDialog::Create.md)|Inicializa el objeto `CDialog`.  Crea un cuadro de diálogo no modal y lo asocia al objeto de `CDialog` .|  
|[CDialog::CreateIndirect](../Topic/CDialog::CreateIndirect.md)|Crea un cuadro de diálogo no modal de una plantilla de cuadro de diálogo en memoria \(no recurso basándose\).|  
|[CDialog::DoModal](../Topic/CDialog::DoModal.md)|Llama a un cuadro de diálogo modal y vuelve cuando termine.|  
|[CDialog::EndDialog](../Topic/CDialog::EndDialog.md)|cierra un cuadro de diálogo modal.|  
|[CDialog::GetDefID](../Topic/CDialog::GetDefID.md)|Obtiene el identificador del control de mismo botón predeterminado para un cuadro de diálogo.|  
|[CDialog::GotoDlgCtrl](../Topic/CDialog::GotoDlgCtrl.md)|Mueve el foco en un control de cuadro de diálogo especificado en el cuadro de diálogo.|  
|[CDialog::InitModalIndirect](../Topic/CDialog::InitModalIndirect.md)|Crea un cuadro de diálogo modal de una plantilla de cuadro de diálogo en memoria \(no recurso basándose\).  Se almacenan los parámetros hasta que se llame a la función `DoModal` .|  
|[CDialog::MapDialogRect](../Topic/CDialog::MapDialogRect.md)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de la pantalla.|  
|[CDialog::NextDlgCtrl](../Topic/CDialog::NextDlgCtrl.md)|Mueve el foco al control de cuadro de diálogo siguiente en el cuadro de diálogo.|  
|[CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)|Reemplace para aumentar la inicialización del cuadro de diálogo.|  
|[CDialog::OnSetFont](../Topic/CDialog::OnSetFont.md)|Reemplace para especificar la fuente que un control de cuadro de diálogo es usar al dibujar el texto.|  
|[CDialog::PrevDlgCtrl](../Topic/CDialog::PrevDlgCtrl.md)|Mueve el foco al control de cuadro de diálogo anterior en el cuadro de diálogo.|  
|[CDialog::SetDefID](../Topic/CDialog::SetDefID.md)|Cambia el control de mismo botón predeterminado para un cuadro de diálogo a un mismo botón especificado.|  
|[CDialog::SetHelpID](../Topic/CDialog::SetHelpID.md)|Establece un identificador de ayuda contextual para el cuadro de diálogo.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialog::OnCancel](../Topic/CDialog::OnCancel.md)|Reemplace para realizar la acción del botón Cancelar o de tecla ESC.  El valor predeterminado se cierra el cuadro de diálogo y **DoModal** devuelve **IDCANCEL**.|  
|[CDialog::OnOK](../Topic/CDialog::OnOK.md)|Reemplace para realizar la acción de botón ACEPTAR en un cuadro de diálogo modal.  El valor predeterminado se cierra el cuadro de diálogo y `DoModal` devuelve **IDOK**.|  
  
## Comentarios  
 los cuadros de diálogo son de dos tipos: modales y no modales.  un cuadro de diálogo modal se debe cerrar por el usuario antes de que la aplicación continúe.  Un cuadro de diálogo no modal permite que el usuario muestre el cuadro de diálogo y vuelva a otra tarea sin la cancelación o quitar del cuadro de diálogo.  
  
 Un objeto de `CDialog` es una combinación de una plantilla y de `CDialog`\- clase derivada del diálogo.  Utilice el editor de cuadros de diálogo para crear la plantilla de cuadro de diálogo y almacenarla en un recurso, utilice el asistente para la clase add para crear una clase derivada de `CDialog`.  
  
 un cuadro de diálogo, como cualquier otra ventana, recibe mensajes de Windows.  En un cuadro de diálogo, está determinado interesado en administrar mensajes de notificación de los controles de cuadro de diálogo puesto que es cómo el usuario interactúa con el cuadro de diálogo.  Utilice la ventana Propiedades para seleccionar qué mensajes desea el identificador y agregará las entradas correspondientes de mapa de mensajes y miembro del controlador de mensajes funciona a la clase.  Sólo es necesario escribir código específico de la aplicación en funciones miembro del controlador.  
  
 Si lo prefiere, puede escribir siempre entradas de mapa de mensajes y las funciones miembro manualmente.  
  
 En todos pero el cuadro de diálogo más trivial, agregará los variables miembro a la clase derivada de diálogo a los datos almacenados escritos en los controles del cuadro de diálogo por el usuario o para mostrar datos del usuario.  Puede utilizar el asistente variable add para crear a variables miembro y para asociarlas con controles.  Al mismo tiempo, se elige un tipo de variable y un intervalo de valores válido para cada variable.  El asistente para código agrega a las variables miembro a la clase derivada del diálogo.  
  
 Un mapa de datos se genera automáticamente para controlar el intercambio de datos entre las variables miembro y los controles de cuadro de diálogo.  El mapa de datos proporciona funciones que se inicializan los controles en el cuadro de diálogo con los valores adecuados, recuperar los datos, y validan los datos.  
  
 Para crear un cuadro de diálogo modal, construya un objeto en el montón mediante el constructor para la clase derivada de diálogo y llame a `DoModal` para crear la ventana cuadro de diálogo y los controles.  Si desea crear un diálogo no modal, llame a **Crear** en el constructor de la clase de diálogo.  
  
 También puede crear una plantilla en memoria utilizando una estructura de datos de [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) como se describe en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  Después de crear un objeto de `CDialog` , llame a [CreateIndirect](../Topic/CDialog::CreateIndirect.md) para crear un cuadro de diálogo no modal, o la llamada [InitModalIndirect](../Topic/CDialog::InitModalIndirect.md) y [DoModal](../Topic/CDialog::DoModal.md) para crear un cuadro de diálogo modal.  
  
 El mapa de datos de intercambio y validación se escribe en un reemplazo de `CWnd::DoDataExchange` que se agregue a la nueva clase de diálogo.  Vea el miembro de [DoDataExchange](../Topic/CWnd::DoDataExchange.md) trabajar en `CWnd` para más en la funcionalidad de intercambio y validación.  
  
 El programador y la llamada `DoDataExchange` de marco indirectamente con una llamada a [CWnd:: UpdateData](../Topic/CWnd::UpdateData.md).  
  
 El marco de trabajo llama a `UpdateData` cuando el usuario hace clic en el botón ACEPTAR para cerrar el cuadro de diálogo modal.  \(Datos de no se recupera si se hace clic en el botón Cancelar\). La implementación predeterminada de [OnInitDialog](../Topic/CDialog::OnInitDialog.md) también llama a `UpdateData` para establecer los valores iniciales de los controles.  Normalmente se reemplaza `OnInitDialog` para inicializar más los controles.  `OnInitDialog` se denomina después de todos los controles de cuadro de diálogo se crea y justo antes del cuadro de diálogo se muestra.  
  
 Puede llamar a `CWnd::UpdateData` en cualquier momento durante la ejecución de un cuadro de diálogo modal o no modal.  
  
 Si desarrolla un cuadro de diálogo a mano, agregue las variables miembro necesarias a la del cuadro de diálogo derivada usted mismo, y agregue funciones miembro para establecer o para obtener estos valores.  
  
 Un cuadro de diálogo modal cierra automáticamente cuando el usuario presiona la los botones ACEPTAR o Cancelar o cuando el código llama a la función miembro de `EndDialog` .  
  
 Al implementar un cuadro de diálogo no modal, reemplace la función miembro de `OnCancel` y llame siempre `DestroyWindow` dentro de.  No llame a la clase base `CDialog::OnCancel`, porque llama `EndDialog`, que hace que el cuadro de diálogo no visibles pero no se destruirá.  También debe reemplazar `PostNcDestroy` para los cuadros de diálogo no modal para eliminar **this**, puesto que los cuadros de diálogo no modal se asignan normalmente con **nuevo**.  Los cuadros de diálogo modales se crean en el cuadro y no necesitan normalmente la limpieza de `PostNcDestroy` .  
  
 Para obtener más información sobre `CDialog`, vea:  
  
-   [Cuadros de diálogo](../../mfc/dialog-boxes.md)  
  
-   Caso Q262954 de Knowledge Base: HOWTO: cree un cuadro de diálogo de Resizeable con las barras de desplazamiento  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo DLGCBR32 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DLGTEMPL de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)