---
title: "CMDIChildWnd Class | Microsoft Docs"
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
  - "CMDIChildWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas secundarias, CMDIChildWnd class"
  - "CMDIChildWnd class"
  - "MDI [C++], ventanas secundarias"
  - "windows [C++], MDI"
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDIChildWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de una ventana secundaria de la interfaz de múltiples documentos \(MDI\) de Windows, junto con los miembros para administrar la ventana.  
  
## Sintaxis  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](../Topic/CMDIChildWnd::CMDIChildWnd.md)|Crea un objeto `CMDIChildWnd`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIChildWnd::Create](../Topic/CMDIChildWnd::Create.md)|Crea una ventana secundaria de MDI Windows asociado al objeto de `CMDIChildWnd` .|  
|[CMDIChildWnd::GetMDIFrame](../Topic/CMDIChildWnd::GetMDIFrame.md)|Devuelve el cuadro primario MDI de la ventana de cliente de MDI.|  
|[CMDIChildWnd::MDIActivate](../Topic/CMDIChildWnd::MDIActivate.md)|Provoca esta ventana MDI secundaria.|  
|[CMDIChildWnd::MDIDestroy](../Topic/CMDIChildWnd::MDIDestroy.md)|Destruye esta ventana MDI secundaria.|  
|[CMDIChildWnd::MDIMaximize](../Topic/CMDIChildWnd::MDIMaximize.md)|Maximiza esta ventana MDI secundaria.|  
|[CMDIChildWnd::MDIRestore](../Topic/CMDIChildWnd::MDIRestore.md)|Restablece esta ventana MDI secundaria de tamaño maximizado o minimizado.|  
|[CMDIChildWnd::SetHandles](../Topic/CMDIChildWnd::SetHandles.md)|Establece los identificadores de recursos de menús y de aceleradores.|  
  
## Comentarios  
 Una ventana MDI secundaria considera una ventana típica de marco, salvo que la ventana MDI secundaria aparece en una ventana de marco MDI en lugar de en el escritorio.  Una ventana MDI secundaria no tiene una barra de menús propio, sino comparte el menú de la ventana de marco MDI.  El marco cambia automáticamente el menú de marco MDI para representar actualmente la ventana MDI secundaria activa.  
  
 Para crear una ventana secundaria útil MDI para la aplicación, derive una clase de `CMDIChildWnd`.  Agregue las variables miembro a la clase derivada a concreto almacenado de datos a la aplicación.  El miembro del controlador de mensajes de implemente funciones y un mapa de mensajes en la clase derivada para especificar lo que ocurre cuando los mensajes se dirigen a la ventana.  
  
 Hay tres maneras de crear una ventana MDI secundaria:  
  
-   Construyala directamente mediante **Crear**.  
  
-   Construyala directamente mediante `LoadFrame`.  
  
-   construyala indirectamente a través de una plantilla de documento.  
  
 Antes de llamar a **Crear** o `LoadFrame`, debe crear el objeto de la ventana de marco en la pila mediante el operador de C\+\+ **nuevo** .  Antes de llamar **Crear** también puede registrar una clase de ventana con la función global de [Clase](../Topic/AfxRegisterWndClass.md) para establecer los estilos de icono y de clase del cuadro.  
  
 Utilice la función miembro de **Crear** para pasar los parámetros de creación de cuadro como argumentos inmediatos.  
  
 `LoadFrame` requiere menos argumentos que **Crear**y, en su lugar recupera la mayoría de los valores predeterminados de recursos, incluida la leyenda del cuadro, el icono, la tabla de aceleradores, y el menú.  para ser accesibles por `LoadFrame`, todos estos recursos deben tener el mismo Id. de recurso \(por ejemplo, **IDR\_MAINFRAME**\).  
  
 Cuando un objeto de `CMDIChildWnd` contiene vistas y documentos, se crean indirectamente el marco en lugar directamente por el programador.  El objeto de `CDocTemplate` orquestra la creación del marco, la creación de vistas que contienen, y la conexión de las vistas al documento adecuado.  Los parámetros de constructor de `CDocTemplate` especifican `CRuntimeClass` de las tres clases implicadas \(documento, cuadro, y vista\).  Un objeto de `CRuntimeClass` se utiliza el marco para crear dinámicamente los nuevos cuadros cuando es especificado por el usuario \(por ejemplo, utilizando el comando de Archivo Nuevo o el comando New de la ventana MDI\).  
  
 Una clase de la ventana de marco derivada de `CMDIChildWnd` se debe declarar con `DECLARE_DYNCREATE` para que el mecanismo anterior de `RUNTIME_CLASS` funcione correctamente.  
  
 La clase de `CMDIChildWnd` hereda gran parte de su implementación predeterminada de `CFrameWnd`.  Para obtener una lista detallada de estas características hace referencia a la clase de [CFrameWnd](../../mfc/reference/cframewnd-class.md) .  la clase de `CMDIChildWnd` tiene las características adicionales siguientes:  
  
-   Junto con la clase de `CMultiDocTemplate` , varios objetos de `CMDIChildWnd` de la misma plantilla de documento comparten el mismo menú, guardar los recursos del sistema de Windows.  
  
-   \- El menú de la ventana secundaria MDI activo reemplaza completamente el menú de la ventana de marco MDI, y la leyenda de actualmente la ventana MDI secundaria activa se agrega actualmente al leyenda MDI de la ventana de marco.  Para otros ejemplos de funciones de ventana MDI secundaria que se implementan junto con una ventana de marco MDI, vea la clase de `CMDIFrameWnd` .  
  
 No utilice el operador de C\+\+ **cancelación** destruir una ventana de marco.  Utilice `CWnd::DestroyWindow` en su lugar.  La implementación de `CFrameWnd` de `PostNcDestroy` eliminará el objeto C\+\+ cuando se destruye la ventana.  Cuando el usuario cierra la ventana de marco, el controlador predeterminado de `OnClose` llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CMDIChildWnd`, vea [cuadro Windows](../../mfc/frame-windows.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo MDIDOCVW de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo SNAPVW de MFC](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd Class](../../mfc/reference/cmdiframewnd-class.md)