---
title: Usar las clases para escribir aplicaciones para Windows | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a8edcabee2f835bd3a3acd0ff3789690764c397
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Usar las clases para escribir aplicaciones para Windows
Tomadas juntas, las clases de la biblioteca (Microsoft Foundation Classes) constituyen un "marco de aplicación," en el que se compila una aplicación para el sistema operativo Windows. En un nivel muy general, el marco de trabajo define el esqueleto de una aplicación y proporciona implementaciones de interfaz de usuario estándar que se pueden colocar en el esqueleto. Su trabajo como programador consiste en rellenar el resto del esqueleto, ¿cuáles son los aspectos que son específicos de la aplicación. Puede obtener una ventaja a la hora mediante el Asistente para aplicaciones MFC para crear los archivos de una aplicación de inicio muy exhaustiva. Utilice los editores de recursos de Microsoft Visual C++ para diseñar los elementos de interfaz de usuario visualmente, comandos de vista de clases para conectar los elementos de código y la biblioteca de clases para implementar la lógica específica de la aplicación.  
  
 Versión 3.0 y versiones posterior del marco de trabajo MFC admite la programación para plataformas de Win32, incluido Microsoft Windows 95 y versiones posteriores y las versiones de Windows NT 3.51 y posteriores. Compatibilidad con Win32 de MFC incluye el subprocesamiento múltiple. Utilice la versión 1.5*x* si tiene que programar aplicaciones de 16 bits.  
  
 Esta serie de artículos presenta una amplia perspectiva del marco de aplicación. También trata sobre los objetos principales que conforman la aplicación y cómo se crean. Entre los temas tratados en estos artículos son los siguientes:  
  
-   [El marco de trabajo](../mfc/framework-mfc.md).  
  
-   División del trabajo entre el marco de trabajo y el código, como se describe en [compilar en el marco](../mfc/building-on-the-framework.md).  
  
-   [La clase de aplicación](../mfc/cwinapp-the-application-class.md), que encapsula la funcionalidad del nivel de aplicación.  
  
-   Cómo [plantillas de documento](../mfc/document-templates-and-the-document-view-creation-process.md) crear y administrar documentos y sus vistas asociadas y ventanas de marco.  
  
-   Clase [CWnd](../mfc/window-objects.md), la clase base raíz de todas las ventanas.  
  
-   [Objetos gráficos](../mfc/graphic-objects.md), como lápices y pinceles.  
  
 Otras partes de framework se incluyen:  
  
-   [Window (objetos): información general](../mfc/window-objects.md)  
  
-   [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)  
  
-   [CObject, la clase Base raíz en MFC](../mfc/using-cobject.md)  
  
-   [Arquitectura documento/vista](../mfc/document-view-architecture.md)  
  
-   [Cuadros de diálogo](../mfc/dialog-boxes.md)  
  
-   [Controles](../mfc/controls-mfc.md)  
  
-   [Barras de control](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Administración de memoria](../mfc/memory-management.md)  
  
     Además de proporcionar una ventaja de escribir aplicaciones para el sistema operativo Windows, MFC también resulta mucho más fácil escribir aplicaciones que utilizan específicamente OLE vincular e incrustar tecnología. Puede realizar la aplicación una OLE visual Editar contenedor, un servidor de edición visual OLE o ambos, y puede agregar automatización para que otras aplicaciones puedan usar los objetos de la aplicación o incluso puedan ejecutarla remotamente.  
  
-   [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
     El kit de desarrollo de control OLE (CDK) está ahora totalmente integrado con el marco de trabajo. Esta serie de artículos proporciona información general sobre el desarrollo de controles ActiveX con MFC. (Los controles ActiveX anteriormente se conocen como controles OLE).  
  
-   [Programación de la base de datos](../data/data-access-programming-mfc-atl.md)  
  
     MFC también proporciona dos conjuntos de clases de base de datos que simplifican la escritura de acceso a datos de aplicaciones. Usando las clases de base de datos ODBC, puede conectarse a bases de datos a través de un controlador de conectividad abierta de base de datos (ODBC), seleccionar los registros de tablas y mostrar información de registro en un formulario en pantalla. Usando las clases de objeto de acceso a datos (DAO), puede trabajar con bases de datos a través del motor de base de datos de Microsoft Jet o los orígenes de datos externos de (que no sean de Jet), incluidos los orígenes de datos ODBC.  
  
     Además, MFC está totalmente habilitado para escribir aplicaciones que utilizan Unicode y juegos de caracteres multibyte (MBCS), juegos de caracteres de específicamente de doble byte (DBCS).  
  
 Para obtener una guía general para la documentación de MFC, vea [temas generales de MFC](../mfc/general-mfc-topics.md).  
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)

