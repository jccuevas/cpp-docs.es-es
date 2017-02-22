---
title: "Caracter&#237;sticas de la interfaz de usuario, Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.ui"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para aplicaciones MFC, características de la interfaz de usuario"
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Caracter&#237;sticas de la interfaz de usuario, Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se explican las opciones que puede utilizar para especificar la apariencia de su aplicación.  Las características de la interfaz de usuario disponibles para el proyecto dependen del tipo de aplicación que haya especificado en la página [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC.  Por ejemplo, si crea una aplicación con una interfaz de un único documento, no podrá agregar estilos de marco secundario.  
  
 **Estilos de marco principal**  
 Establece las características del marco de ventana principal de la aplicación.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Marco grueso**|Crea una ventana con un borde de tamaño ajustable.  El valor predeterminado.|  
|**Cuadro minimizar**|Incluye un cuadro para minimizar en la ventana de marco principal.  El valor predeterminado.|  
|**Cuadro maximizar**|Incluye un cuadro para maximizar en la ventana de marco principal.  El valor predeterminado.|  
|**Minimizada**|Abre la ventana de marco principal como un icono.|  
|**Maximizada**|Abre la ventana de marco principal con el tamaño total de la pantalla.|  
|**Menú del sistema**|Incluye un menú del sistema en la ventana de marco principal.  El valor predeterminado.|  
|**Cuadro de diálogo Acerca de**|Incluye un cuadro **Acerca de** para la aplicación.  El usuario puede tener acceso a este cuadro en el menú **Ayuda** de la aplicación.  La opción se encuentra activada de forma predeterminada y no se puede modificar a menos que seleccione **Basado en cuadros de diálogo** en la página [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md).<br /><br /> **Nota** Generalmente, una opción no disponible indica que el asistente no aplica la opción al proyecto, independientemente de si la casilla del elemento no disponible está activada o no.  En este caso, el asistente agrega siempre un cuadro de diálogo **Acerca de** al proyecto, a menos que especifique primero que el proyecto está basado en un cuadro de diálogo y después desactive la casilla.|  
|**Barra de estado inicial**|Agrega una barra de estado a la aplicación.  La barra de estado contiene indicadores automáticos para las teclas BLOQ MAYÚS, BLOQ NUM y BLOQ DESPL del teclado, y una línea de mensaje que muestra cadenas de ayuda para los comandos de menú y los botones de barra de herramientas.  Si hace clic en esta opción también agrega comandos de menú para mostrar u ocultar la barra de estado.  De manera predeterminada, las aplicaciones tienen una barra de estado.  No está disponible para tipos de aplicación basados en cuadros de diálogo.|  
|**Ventana divisora**|Proporciona una barra divisora.  La barra divisora separa las vistas principales de la aplicación.  En una aplicación de interfaz de múltiples documentos \(MDI\), la ventana de cliente del marco secundario MDI es una ventana divisora, y en una aplicación de interfaz de un único documento \(SDI\) o una aplicación de múltiples documentos de nivel superior, la ventana cliente del marco principal es una ventana divisora.  No está disponible para tipos de aplicación basados en cuadros de diálogo.|  
  
 **Estilos de marco secundario**  
 Especifica la apariencia y el estado inicial de los marcos secundarios de la aplicación.  Los estilos de marco secundario sólo están disponibles para aplicaciones MDI.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Cuadro de minimizar secundario**|Especifica si una ventana secundaria tiene un botón Minimizar \(habilitado de forma predeterminada\).|  
|**Cuadro de maximizar secundario**|Especifica si una ventana secundaria tiene un botón Maximizar \(habilitado de forma predeterminada\).|  
|**Maximizado secundario**|Especifica si una ventana secundaria se maximiza inicialmente estableciendo el marcador de cs.style **WS\_MAXIMIZE** en la función miembro [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) de `CChildFrame`.|  
  
 **Barras de comandos \(menú\/barra de herramientas\/cinta de opciones\)**  
 Indica si la aplicación incluye menús, barras de herramientas y\/o una cinta de opciones.  No está disponible para aplicaciones basadas en cuadros de diálogo.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Usar un menú clásico**|Especifica que la aplicación contiene un menú clásico no arrastrable.|  
|**Usar una barra de herramientas acoplable clásica**|Agrega una barra de herramientas estándar de Windows a la aplicación.  La barra de herramientas contiene botones para crear un documento nuevo, abrir y guardar archivos de documento, cortar, copiar, pegar o imprimir texto, y pasar a modo de Ayuda.  Si habilita esta opción también agrega comandos de menú para mostrar u ocultar la barra de herramientas.|  
|**Usar una barra de herramientas de estilo explorador**|Agrega a la aplicación una barra de herramientas estilo Internet Explorer.|  
|**Usar una barra de menús y una barra de herramientas**|Indica que la aplicación contiene una barra de menús y una barra de herramientas arrastrables.|  
|**Barras de herramientas e imágenes definidas por el usuario**|Permite al usuario personalizar la barra de herramientas y las imágenes de la barra de herramientas en tiempo de ejecución.|  
|**Comportamiento de menús personalizado**|Especifica si el menú contiene la lista completa de elementos al abrirse o si solo contiene los comandos que el usuario utiliza con frecuencia.|  
|**Utilizar una cinta de opciones**|Utiliza una cinta de opciones similar a la de Office 2007 en la aplicación en lugar de una barra de menús o una barra de herramientas.|  
  
 **Título del cuadro de diálogo**  
 Para aplicaciones basadas únicamente en [CDialog Class](../../mfc/reference/cdialog-class.md), este título aparecerá en la barra de título del cuadro de diálogo.  Para modificar este campo, debe seleccionar primero la opción **Basado en cuadros de diálogo** en **Tipo de aplicación**.  Para obtener más información, vea [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)