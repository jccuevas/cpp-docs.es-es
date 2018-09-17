---
title: Características de la interfaz de usuario, Asistente para aplicaciones MFC | Microsoft Docs
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
ms.openlocfilehash: 29961e7b597683d3735203de9a47646b2a320469
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722558"
---
# <a name="user-interface-features-mfc-application-wizard"></a>Características de la interfaz de usuario, Asistente para aplicaciones MFC

En este tema se explica las opciones que puede usar para especificar el aspecto de la aplicación. Las características de interfaz de usuario disponibles para el proyecto dependen del tipo de aplicación que haya especificado en el [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) página del Asistente para aplicaciones MFC. Por ejemplo, si crea una aplicación de interfaz de único documento, no se puede agregar estilos de marco secundario.  
  
- **Estilos de marco principal**

   Establece las características del marco de ventana principal de la aplicación.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Marco grueso**|Crea una ventana que tiene un borde de tamaño. El valor predeterminado.|  
   |**Minimizar cuadro**|Incluye un cuadro Minimizar en la ventana de marco principal. El valor predeterminado.|  
   |**Maximizar el cuadro**|Incluye un cuadro para maximizar en la ventana de marco principal. El valor predeterminado.|  
   |**Minimizado**|Abre la ventana de marco principal como un icono.|  
   |**Maximizado**|Se abre la ventana de marco principal para el tamaño de la pantalla completa.|  
   |**Menú del sistema**|Incluye un menú del sistema en la ventana de marco principal. El valor predeterminado.|  
   |**Cuadro acerca de**|Incluye un **sobre** para la aplicación. El usuario puede acceder a este cuadro de la aplicación **ayuda** menú. El valor predeterminado y puede cambiar a menos que seleccione **en función del cuadro de diálogo**, en el [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) página.<br /><br /> **Tenga en cuenta** por lo general, una opción no disponible indica que el asistente no aplica la opción al proyecto, si la casilla del elemento no disponible está activada o desactivada. En este caso, el asistente agrega siempre un **sobre** cuadro en el proyecto, a menos que especifique primero el proyecto como en función del cuadro de diálogo y, a continuación, desactive la casilla.|  
   |**Barra de estado inicial**|Agrega una barra de estado a la aplicación. La barra de estado contiene indicadores automática para las claves del teclado de BLOQ MAYÚS, BLOQ NUM y Bloq Despl y cadenas de una línea de mensaje que muestra la ayuda para comandos de menú y barra de herramientas de botones. Al hacer clic en esta opción, también se agrega los comandos de menú para mostrar u ocultar la barra de estado. De forma predeterminada, una aplicación tiene una barra de estado. No está disponible para los tipos de aplicación basada en el cuadro de diálogo.|  
   |**Ventana dividida**|Proporciona una barra divisora. La barra de división divide vistas principales de la aplicación. En una aplicación de múltiples documentos (MDI) de la interfaz, ventana de cliente del marco MDI secundario es una ventana divisora y, en una aplicación de único documento (SDI) de la interfaz y la aplicación de múltiples documentos de nivel superior, la ventana de cliente del marco principal es una ventana divisora. No está disponible para los tipos de aplicación basada en el cuadro de diálogo.|  
  
- **Estilos de marco secundario**

   Especifica la apariencia y el estado inicial de los marcos secundarios en la aplicación. Estilos de marco secundario están disponibles para las aplicaciones MDI.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Cuadro de minimizar secundario**|Especifica si una ventana secundaria tiene un botón Minimizar (habilitado de forma predeterminada).|  
   |**Cuadro de maximizar secundario**|Especifica si una ventana secundaria tiene un botón Maximizar (habilitado de forma predeterminada).|  
   |**Maximizado secundario**|Especifica si una ventana secundaria se maximiza inicialmente estableciendo el cs.style marca WS_MAXIMIZE en el [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) función miembro de `CChildFrame`.|  
  
- **Barras de comandos (menú o barra de herramientas o cinta)**

   Indica si la aplicación incluye menús, barras de herramientas o una cinta de opciones. No está disponible para las aplicaciones basadas en el cuadro de diálogo.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Usar un menú clásico**|Especifica que la aplicación contiene un menú clásico, no se pueden arrastrar.|  
   |**Usar una barra de herramientas acoplable clásica**|Agrega una barra de herramientas estándar de Windows a la aplicación. La barra de herramientas contiene botones para crear un nuevo documento; Abrir y guardar archivos de documento; Cortar, copiar, pegar o imprimir texto; y entrar en modo de ayuda. Al habilitar esta opción, también agrega los comandos de menú para mostrar u ocultar la barra de herramientas.|  
   |**Usar una barra de herramientas de estilo de explorador**|Agrega una barra de herramientas de estilo de Internet Explorer a la aplicación.|  
   |**Usar una barra de menú y barra de herramientas**|Indica que la aplicación contiene una barra de menús arrastrable y una barra de herramientas.|  
   |**Las imágenes y las barras de herramientas definidas por el usuario**|Permite al usuario personalizar la barra de herramientas y las imágenes de barra de herramientas en tiempo de ejecución.|  
   |**Comportamiento de menú personalizado**|Especifica si el menú contiene la lista completa de elementos al abrirse, o si contiene únicamente los comandos que el usuario utiliza con más frecuencia.|  
   |**Usar una cinta de opciones**|Utiliza una cinta de opciones similar a Office 2007 en la aplicación en lugar de una barra de menús o barra de herramientas.|  
  
- **Título del cuadro de diálogo**

   Para [CDialog (clase)](../../mfc/reference/cdialog-class.md)-aplicaciones basadas únicamente en, este título aparece en la barra de título del cuadro de diálogo. Para editar este campo, primero debe seleccionar la **en función del cuadro de diálogo** opción **tipo de aplicación**. Para obtener más información, consulte [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)

