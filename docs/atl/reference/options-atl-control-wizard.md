---
title: "Opciones, Asistente para controles ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ATL, opciones"
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Opciones, Asistente para controles ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Insertar aquí el resumen de "Resultados de la búsqueda".  
  
 Utilice esta página del asistente para definir el tipo de control que está creando y el nivel de compatibilidad con interfaces que contiene.  
  
## Lista de UIElement  
 **Tipo de control**  
 Tipo de control que se desea crear.  
  
-   **Control estándar: un control ActiveX.**  
  
-   **Control compuesto**: un control ActiveX que puede contener \(al igual que un cuadro de diálogo\) otros controles ActiveX o controles de Windows.  Un control compuesto incluye lo siguiente:  
  
    -   Una plantilla para el cuadro de diálogo que implementa el control compuesto.  
  
    -   Un recurso personalizado, REGISTRY, que registra automáticamente el control compuesto al invocarlo.  
  
    -   Una clase en C\+\+ que implementa el control compuesto.  
  
    -   Una interfaz COM, expuesta por el control compuesto.  
  
    -   Una página de prueba HTML que contiene el control compuesto.  
  
     De forma predeterminada, este control establece [CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md) en true para indicar que se trata de un control con ventana.  Implementa un mapa de recepción de eventos.  Para obtener más información, vea [Compatibilidad con controles DHTML](../../atl/atl-support-for-dhtml-controls.md).  
  
-   **Control DHTML**: un control DTHML ATL especifica la interfaz de usuario mediante HTML.  La clase de UI DHTML contiene un mapa COM.  De forma predeterminada, este control establece [CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md) en true para indicar que se trata de un control con ventana.  
  
     Para obtener más información, vea [Identifying the Elements of the DHTML Control Project](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
 **Control mínimo**  
 Sólo admite las interfaces que se requieren de forma imprescindible por parte de la mayoría de los contenedores.  Se puede establecer el **Control mínimo** para cualquier tipo de control; es posible crear un control mínimo estándar, un control mínimo compuesto, o un control mínimo DHTML.  
  
 **Agregación**  
 Agrega compatibilidad con la agregación para el control que se está creando.  Para obtener más información, vea [Aggregation](../../atl/aggregation.md).  
  
-   **Sí**: crea un control que puede agregarse.  
  
-   **No**: crea un control que no puede agregarse.  
  
-   **Sólo**: crea un control del que sólo se pueden crear instancias mediante agregación.  
  
 **Modelo de subprocesos**  
 Especifica el modelo de subprocesos usado por el control.  
  
-   **Único**: el control sólo se ejecutará únicamente en el subproceso COM principal.  
  
-   **Apartamento**: el control puede crearse en cualquier subprocesamiento controlado simple.  Es el formato predeterminado.  
  
 **Interfaz**  
 Tipo de interfaz que expone este control al contenedor.  
  
-   **Doble**: crea una interfaz que expone propiedades y métodos a través de `IDispatch` y directamente a través de VTBL.  
  
-   **Personalizada**: crea una interfaz que expone métodos directamente a través de VTBL.  
  
     Si selecciona **Personalizada**, puede especificar que el control sea **Compatible con automatización**.  Si selecciona **Compatible con automatización**, el asistente agrega el atributo [oleautomation](../../windows/oleautomation.md) a la interfaz en el archivo IDL, y el contador de referencias universal puede calcular las referencias de la interfaz en oleaut32.dll.  Vea [Detalles del cálculo de referencias](http://msdn.microsoft.com/library/windows/desktop/ms692621) en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] para obtener más información.  
  
     Asimismo, si selecciona **Compatible con automatización**, todos los parámetros de todos los métodos del control deben ser compatibles con **VARIANT**.  
  
 **Compatibilidad**  
 Establece diversas compatibilidades adicionales para el control.  
  
-   **Puntos de conexión**: habilita puntos de conexión para el objeto al hacer que su clase correspondiente se derive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) y permitir que exponga una interfaz de origen.  
  
-   **Con licencia**: agrega al control compatibilidad con [licencias](http://msdn.microsoft.com/library/windows/desktop/ms690543).  Los controles con licencia sólo pueden hospedarse si el equipo cliente posee la licencia adecuada.  
  
## Vea también  
 [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)