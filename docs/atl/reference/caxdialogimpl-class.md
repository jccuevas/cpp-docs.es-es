---
title: "CAxDialogImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAxDialogImpl"
  - "ATL.CAxDialogImpl"
  - "CAxDialogImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, cuadros de diálogo"
  - "CAxDialogImpl class"
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAxDialogImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa un cuadro de diálogo \(modal o no modal\) que los controles ActiveX de hospeda.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class TBase= CWindow  
>  
class ATL_NO_VTABLE CAxDialogImpl :  
public CDialogImplBaseT< TBase>  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `CAxDialogImpl`.  
  
 *TBase*  
 la clase de ventana base para **CDialogImplBaseT**.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](../Topic/CAxDialogImpl::AdviseSinkMap.md)|Llame a este método para advertir o el unadvise todas las entradas en el mapa del evento del mapa del receptor del objeto.|  
|[CAxDialogImpl::Create](../Topic/CAxDialogImpl::Create.md)|Llame a este método para crear un cuadro de diálogo no modal.|  
|[CAxDialogImpl::DestroyWindow](../Topic/CAxDialogImpl::DestroyWindow.md)|Llame a este método para destruir un cuadro de diálogo no modal.|  
|[CAxDialogImpl::DoModal](../Topic/CAxDialogImpl::DoModal.md)|Llame a este método para crear un cuadro de diálogo modal.|  
|[CAxDialogImpl::EndDialog](../Topic/CAxDialogImpl::EndDialog.md)|Llame a este método para destruir un cuadro de diálogo modal.|  
|[CAxDialogImpl::GetDialogProc](../Topic/CAxDialogImpl::GetDialogProc.md)|Llame a este método para obtener un puntero a la función de devolución de llamada de `DialogProc` .|  
|[CAxDialogImpl::GetIDD](../Topic/CAxDialogImpl::GetIDD.md)|Llame a este método para obtener el Id. de recurso de plantilla de cuadro de diálogo|  
|[CAxDialogImpl::IsDialogMessage](../Topic/CAxDialogImpl::IsDialogMessage.md)|Llame a este método para determinar si un mensaje está diseñado para este cuadro de diálogo y, si lo es, procesa el mensaje.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAxDialogImpl::m\_bModal](../Topic/CAxDialogImpl::m_bModal.md)|Una variable que sólo existe en versiones de depuración y se establece en true si el cuadro de diálogo es modal.|  
  
## Comentarios  
 `CAxDialogImpl` permite crear un cuadro de diálogo modal o no modal.  `CAxDialogImpl` proporciona el procedimiento del cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para enviar mensajes a los controladores adecuados.  
  
 `CAxDialogImpl` deriva de `CDialogImplBaseT`, que a su vez deriva de *TBase* \(de forma predeterminada, `CWindow`\) y de `CMessageMap`.  
  
 La clase debe definir un miembro de IDD que especifica el identificador de recurso de plantilla de cuadro de diálogo  Por ejemplo, agregando un objeto de diálogo ATL mediante el cuadro de diálogo **Agregar clase** agrega automáticamente la línea siguiente a la clase:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/CPP/caxdialogimpl-class_1.h)]  
  
 donde es **nombre corto**`MyDialog` escrito en el asistente para cuadros de diálogo ATL.  
  
 Vea [implementar un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.  
  
 Tenga en cuenta que un control ActiveX en un cuadro de diálogo modal creado con `CAxDialogImpl` no admitirá las teclas de aceleración.  Para admitir las teclas de aceleración de un cuadro de diálogo creado con `CAxDialogImpl`, cree un cuadro de diálogo no modal y, mediante dispone del bucle de mensajes, utilice [CAxDialogImpl:: IsDialogMessage](../Topic/CAxDialogImpl::IsDialogMessage.md) después de obtener un mensaje de la cola para controlar una tecla de aceleración.  
  
 Para obtener más información sobre `CAxDialogImpl`, vea [Preguntas más frecuentes sobre la contención de controles ATL](../../atl/atl-control-containment-faq.md).  
  
## Jerarquía de herencia  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [CDialogImpl Class](../../atl/reference/cdialogimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)