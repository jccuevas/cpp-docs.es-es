---
title: Características de la interfaz de usuario, Asistente para aplicaciones MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42196e437c8ff2ee43f733e1826b2a19c5dbb0a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="user-interface-features-mfc-application-wizard"></a>Características de la interfaz de usuario, Asistente para aplicaciones MFC
En este tema se explica las opciones que puede usar para especificar la apariencia de la aplicación. Las características de interfaz de usuario disponibles para el proyecto dependen del tipo de aplicación que haya especificado en el [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) página del Asistente para aplicaciones MFC. Por ejemplo, si crea una aplicación de interfaz de único documento, no se puede agregar estilos de marco secundario.  
  
 **Estilos de marco principal**  
 Establece las características del marco de ventana principal de la aplicación.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Marco grueso**|Crea una ventana que tiene un borde de tamaño. El valor predeterminado.|  
|**Minimizar cuadro**|Incluye un cuadro para minimizar en la ventana de marco principal. El valor predeterminado.|  
|**Maximizar el cuadro**|Incluye un cuadro para maximizar en la ventana de marco principal. El valor predeterminado.|  
|**Minimizado**|Abre la ventana de marco principal como un icono.|  
|**Maximizado**|Abre la ventana de marco principal para el tamaño completo de la pantalla.|  
|**Menú del sistema**|Incluye un menú de sistema en la ventana de marco principal. El valor predeterminado.|  
|**Cuadro acerca de**|Incluye un **sobre** cuadro de la aplicación. El usuario puede tener acceso a este cuadro de la aplicación **ayuda** menú. El valor predeterminado y puede cambiar a menos que seleccione **diálogo según**, en la [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) página.<br /><br /> **Tenga en cuenta** por lo general, una opción no disponible indica que el asistente no aplica la opción al proyecto, si se selecciona o se desactiva la casilla del elemento no está disponible. En este caso, el asistente agrega siempre un **sobre** cuadro en el proyecto, a menos que especifique primero el proyecto como en función del cuadro de diálogo y, a continuación, desactive la casilla.|  
|**Barra de estado inicial**|Agrega una barra de estado a la aplicación. La barra de estado contiene indicadores automáticos para las claves del teclado de BLOQ MAYÚS, BLOQ NUM y Bloq Despl y las cadenas de una línea de mensaje que muestra la ayuda para comandos de menú y barra de herramientas de botones. Al hacer clic en esta opción, también se agrega comandos de menú para mostrar u ocultar la barra de estado. De forma predeterminada, una aplicación tiene una barra de estado. No está disponible para los tipos de aplicación basada en el cuadro de diálogo.|  
|**Ventana dividida**|Proporciona una barra divisora. La barra de división divide vistas principales de la aplicación. En una aplicación de múltiples documentos (MDI) de la interfaz, ventana de cliente del marco MDI secundario es una ventana divisora, y en una aplicación de único documento (SDI) de la interfaz y aplicación de múltiples documentos de nivel superior, la ventana de cliente del marco principal es una ventana divisora. No está disponible para los tipos de aplicación basada en el cuadro de diálogo.|  
  
 **Estilos de marco secundario**  
 Especifica la apariencia y el estado inicial de los marcos secundarios en la aplicación. Estilos de marco secundario están disponibles para las aplicaciones MDI.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Cuadro de minimizar secundario**|Especifica si una ventana secundaria tiene un botón Minimizar (habilitado de forma predeterminada).|  
|**Cuadro de maximizar secundario**|Especifica si una ventana secundaria tiene un botón Maximizar (habilitado de forma predeterminada).|  
|**Maximizado secundario**|Especifica si una ventana secundaria se maximiza inicialmente estableciendo el indicador cs.style **WS_MAXIMIZE** en el [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) función miembro de `CChildFrame`.|  
  
 **Barras de comandos (menú/barra de herramientas/cinta de opciones)**  
 Indica si la aplicación incluye menús, barras de herramientas o una cinta de opciones. No está disponible para aplicaciones basadas en el cuadro de diálogo.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Usar un menú clásico**|Especifica que la aplicación contiene un menú clásico, no se pueden arrastrar.|  
|**Usar una barra de herramientas de acoplamiento clásica**|Agrega una barra de herramientas estándar de Windows a la aplicación. La barra de herramientas contiene botones para crear un nuevo documento; Abrir y guardar archivos de documento; Cortar, copiar, pegar o imprimir texto; y entrar en el modo de ayuda. Si se habilita esta opción, también agrega comandos de menú para mostrar u ocultar la barra de herramientas.|  
|**Usar una barra de herramientas de estilo de explorador**|Agrega una barra de herramientas de estilo de Internet Explorer a la aplicación.|  
|**Usar una barra de menús y barra de herramientas**|Indica que la aplicación contiene una barra de menús arrastrable y una barra de herramientas.|  
|**Las imágenes y las barras de herramientas definidas por el usuario**|Permite al usuario personalizar la barra de herramientas y las imágenes de barra de herramientas en tiempo de ejecución.|  
|**Comportamiento de menús personalizado**|Especifica si el menú contiene la lista completa de elementos al abrirse, o si contiene solo los comandos que el usuario utiliza con más frecuencia.|  
|**Usar una cinta de opciones**|Utiliza una cinta de opciones de Office 2007 similar en la aplicación en lugar de una barra de menús o barra de herramientas.|  
  
 **Título del cuadro de diálogo**  
 Para [CDialog (clase)](../../mfc/reference/cdialog-class.md)-aplicaciones basadas únicamente en, este título aparecerá en la barra de título del cuadro de diálogo. Para editar este campo, primero debe seleccionar la **diálogo según** opción **tipo de aplicación**. Para obtener más información, consulte [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)

