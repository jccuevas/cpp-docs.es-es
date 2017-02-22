---
title: "CComCompositeControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComCompositeControl"
  - "ATL::CComCompositeControl"
  - "ATL.CComCompositeControl<T>"
  - "ATL.CComCompositeControl"
  - "ATL::CComCompositeControl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCompositeControl class"
  - "controles compuestos, CComCompositeControl class"
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComCompositeControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona los métodos necesarios para implementar un control compuesto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T   
>  
class CComCompositeControl :  
public CComControl< T, CAxDialogImpl< T > >  
```  
  
#### Parámetros  
 `T`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir para el control compuesto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](../Topic/CComCompositeControl::CComCompositeControl.md)|el constructor.|  
|[CComCompositeControl::~CComCompositeControl](../Topic/CComCompositeControl::~CComCompositeControl.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)|Llame a este método para advertir o el unadvise todos los controles de hospedados por el control compuesto.|  
|[CComCompositeControl::CalcExtent](../Topic/CComCompositeControl::CalcExtent.md)|Llame a este método para calcular el tamaño en unidades de **HIMETRIC** de recursos de cuadro de diálogo utilizado para hospedar el control compuesto.|  
|[CComCompositeControl::Create](../Topic/CComCompositeControl::Create.md)|Se llama a este método para crear la ventana de control para el control compuesto.|  
|[CComCompositeControl::CreateControlWindow](../Topic/CComCompositeControl::CreateControlWindow.md)|Llame a este método para crear la ventana de control y notificárselo cualquier control hospedado.|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](../Topic/CComCompositeControl::SetBackgroundColorFromAmbient.md)|Llame a este método para establecer el color de fondo del control compuesto utilizando el color de fondo del contenedor.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCompositeControl::m\_hbrBackground](../Topic/CComCompositeControl::m_hbrBackground.md)|Pincel del fondo.|  
|[CComCompositeControl::m\_hWndFocus](../Topic/CComCompositeControl::m_hWndFocus.md)|Identificador de la ventana que tiene el foco.|  
  
## Comentarios  
 Las clases derivadas de la clase `CComCompositeControl` hereda la funcionalidad de un control compuesto de ActiveX.  Los controles ActiveX derivados de `CComCompositeControl` se hospedan en un cuadro de diálogo estándar.  Se llama a estos tipos de controles controles compuestos porque pueden hospedar otros controles \(controles nativos de Windows y controles ActiveX\).  
  
 `CComCompositeControl` identifica el recurso de cuadro de diálogo para utilizarlo para crear el control compuesto buscando un miembro de datos de la clase secundaria.  Establece el miembro IDD de esta clase secundaria al Id. de recurso de recursos de cuadro de diálogo que se utilizará como ventana de control.  A continuación se muestra un ejemplo del miembro de datos que la clase derivada de `CComCompositeControl` debe contener para identificar el recurso de cuadro de diálogo que se utilizará para la ventana de control:  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/CPP/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  Los controles compuestos siempre son controles con, aunque pueden contener controles sin ventana.  
  
 Un control implementado por `CComCompositeControl`\- la clase derivada tiene comportamiento de tabulación predeterminado integrado.  Cuando el control recibe el foco por ser con fichas en una aplicación que contiene, sucesivamente presionar la tecla TAB provocará el foco que se completará un ciclo a través de los controles contenidos de todo el control compuesto, después del control compuesto y al elemento siguiente en el orden de la pestaña del contenedor.  El orden de la pestaña de los controles de hospedados es determinado por el recurso de cuadro de diálogo y determina el orden en que el desplazamiento aparecerá.  
  
> [!NOTE]
>  Para que los aceleradores funcionan correctamente con `CComCompositeControl`, es necesario cargar una tabla de aceleradores como se crea el control, pasa el identificador y el número de aceleradores de nuevo [IOleControlImpl::GetControlInfo](../Topic/IOleControlImpl::GetControlInfo.md)y, finalmente destruye la tabla cuando se suelta el control.  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/CPP/ccomcompositecontrol-class_2.h)]  
  
## Jerarquía de herencia  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)   
 [Class Overview](../../atl/atl-class-overview.md)