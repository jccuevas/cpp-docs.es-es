---
title: "CMDIFrameWnd Class | Microsoft Docs"
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
  - "CMDIFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIFrameWnd class"
  - "MDI frame windows"
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDIFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de una ventana de marco \(MDI\) de interfaz de múltiples documentos de Windows, junto con los miembros para administrar la ventana.  
  
## Sintaxis  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](../Topic/CMDIFrameWnd::CMDIFrameWnd.md)|Construye un `CMDIFrameWnd`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](../Topic/CMDIFrameWnd::CreateClient.md)|crea una ventana de Windows **MDICLIENT** para este `CMDIFrameWnd`.  Llama a la función miembro de `OnCreate` de `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](../Topic/CMDIFrameWnd::CreateNewChild.md)|crea una nueva ventana secundaria.|  
|[CMDIFrameWnd::GetWindowMenuPopup](../Topic/CMDIFrameWnd::GetWindowMenuPopup.md)|devuelve el menú emergente de la ventana.|  
|[CMDIFrameWnd::MDIActivate](../Topic/CMDIFrameWnd::MDIActivate.md)|Genera otra ventana MDI secundaria.|  
|[CMDIFrameWnd::MDICascade](../Topic/CMDIFrameWnd::MDICascade.md)|Organiza todas las ventanas secundarias en un formato en cascada.|  
|[CMDIFrameWnd::MDIGetActive](../Topic/CMDIFrameWnd::MDIGetActive.md)|Recupera actualmente la ventana MDI secundaria activa, junto con una marca que indica si maximizan al elemento secundario.|  
|[CMDIFrameWnd::MDIIconArrange](../Topic/CMDIFrameWnd::MDIIconArrange.md)|Organiza todas las ventanas secundarias minimizadas del documento.|  
|[CMDIFrameWnd::MDIMaximize](../Topic/CMDIFrameWnd::MDIMaximize.md)|Maximiza una ventana MDI secundaria.|  
|[CMDIFrameWnd::MDINext](../Topic/CMDIFrameWnd::MDINext.md)|Activa la ventana secundaria inmediatamente detrás actualmente la ventana secundaria activa y coloca actual de la ventana secundaria activa detrás de las demás ventanas secundarias.|  
|[CMDIFrameWnd::MDIPrev](../Topic/CMDIFrameWnd::MDIPrev.md)|Activa la ventana secundaria anterior y coloca actualmente la ventana secundaria activa inmediatamente detrás de ella.|  
|[CMDIFrameWnd::MDIRestore](../Topic/CMDIFrameWnd::MDIRestore.md)|Restaura una ventana MDI secundaria de tamaño maximizado o minimizado.|  
|[CMDIFrameWnd::MDISetMenu](../Topic/CMDIFrameWnd::MDISetMenu.md)|Reemplaza el menú de una ventana de marco MDI, en el menú emergente de ventana, o ambos.|  
|[CMDIFrameWnd::MDITile](../Topic/CMDIFrameWnd::MDITile.md)|Organiza todas las ventanas secundarias en un formato de mosaico.|  
  
## Comentarios  
 Para crear una ventana útil de marco MDI para la aplicación, derive una clase de `CMDIFrameWnd`.  Agregue las variables miembro a la clase derivada a concreto almacenado de datos a la aplicación.  El miembro del controlador de mensajes de implemente funciones y un mapa de mensajes en la clase derivada para especificar lo que ocurre cuando los mensajes se dirigen a la ventana.  
  
 Puede crear una ventana de marco MDI llamando a funciones miembro de [Crear](../Topic/CFrameWnd::Create.md) o de [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) de `CFrameWnd`.  
  
 Antes de llamar a **Crear** o `LoadFrame`, debe crear el objeto de la ventana de marco en la pila mediante el operador de C\+\+ **nuevo** .  Antes de llamar **Crear** también puede registrar una clase de ventana con la función global de [Clase](../Topic/AfxRegisterWndClass.md) para establecer los estilos de icono y de clase del cuadro.  
  
 Utilice la función miembro de **Crear** para pasar los parámetros de creación de cuadro como argumentos inmediatos.  
  
 `LoadFrame` requiere menos argumentos que **Crear**y, en su lugar recupera la mayoría de los valores predeterminados de recursos, incluida la leyenda del cuadro, el icono, la tabla de aceleradores, y el menú.  Para obtener acceso a `LoadFrame`, todos estos recursos deben tener el mismo Id. de recurso \(por ejemplo, **IDR\_MAINFRAME**\).  
  
 Aunque **MDIFrameWnd** es derivado de `CFrameWnd`, una clase de ventana de marco derivada de `CMDIFrameWnd` no necesita declararse con `DECLARE_DYNCREATE`.  
  
 La clase de `CMDIFrameWnd` hereda gran parte de su implementación predeterminada de `CFrameWnd`.  Para obtener una lista detallada de estas características, vea la descripción de la clase de [CFrameWnd](../../mfc/reference/cframewnd-class.md) .  la clase de `CMDIFrameWnd` tiene las características adicionales siguientes:  
  
-   Una ventana de marco MDI administra la ventana de **MDICLIENT** , colocándolo de nuevo junto con las barras de controles.  La ventana de cliente MDI es el elemento primario directo de las ventanas secundarias de marco MDI.  Los estilos de ventana de **WS\_HSCROLL** y de **WS\_VSCROLL** especificadas en `CMDIFrameWnd` se aplican a la ventana de cliente de MDI en lugar de la ventana de marco principal para que el usuario puede cambiar el área de cliente MDI \(como en el administrador de programas de Windows, por ejemplo\).  
  
-   Una ventana de marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ninguna ventana secundaria de MDI activa.  Cuando hay un elemento secundario de MDI activa, la barra de menús de MDI de la ventana de marco automáticamente se reemplaza por el menú de la ventana MDI secundaria.  
  
-   Una ventana de marco MDI funciona junto con la ventana secundaria actual de MDI, si la hay.  Por ejemplo, los mensajes de comando se delegan actualmente el formulario secundario MDI activo antes de la ventana de marco MDI.  
  
-   Una ventana de marco MDI tiene controladores predeterminados para los comandos del menú Ventana estándar siguientes:  
  
    -   **ID\_WINDOW\_TILE\_VERT**  
  
    -   **ID\_WINDOW\_TILE\_HORZ**  
  
    -   **ID\_WINDOW\_CASCADE**  
  
    -   **ID\_WINDOW\_ARRANGE**  
  
-   Una ventana de marco MDI también tiene una implementación de **ID\_WINDOW\_NEW**, que crea un nuevo cuadro y vista en el documento actual.  Una aplicación puede reemplazar estas implementaciones predeterminadas de comando para personalizar el control de la ventana MDI.  
  
 No utilice el operador de C\+\+ **cancelación** destruir una ventana de marco.  Utilice `CWnd::DestroyWindow` en su lugar.  La implementación de `CFrameWnd` de `PostNcDestroy` eliminará el objeto C\+\+ cuando se destruye la ventana.  Cuando el usuario cierra la ventana de marco, el controlador predeterminado de `OnClose` llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CMDIFrameWnd`, vea [cuadro Windows](../../mfc/frame-windows.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo MDIDOCVW de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo SNAPVW de MFC](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)