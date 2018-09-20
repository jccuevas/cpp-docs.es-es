---
title: Usar las clases para escribir aplicaciones para Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c60cf5d6f61f16aac18524e8b6e75638ec13d27e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433340"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Usar las clases para escribir aplicaciones para Windows

Tomadas juntas, las clases de la biblioteca Microsoft Foundation Class (MFC) constituyen un "marco de aplicación," en el que se compila una aplicación para el sistema operativo Windows. En un nivel muy general, el marco de trabajo define el esqueleto de una aplicación y proporciona implementaciones de interfaz de usuario estándar que se pueden colocar en el esqueleto. Su trabajo como programador consiste en rellenar el resto del esqueleto, cuáles son esas cosas que son específicas de la aplicación. Puede obtener una ventaja mediante el Asistente para aplicaciones MFC para crear los archivos de una aplicación muy exhaustivo starter. Utilice los editores de recursos de Microsoft Visual C++ para diseñar los elementos de interfaz de usuario visualmente, comandos de vista de clases para conectar dichos elementos con código y la biblioteca de clases para implementar la lógica específica de la aplicación.

Versión 3.0 y versiones posterior del marco de trabajo MFC es compatible con la programación para las plataformas de Win32, incluido Microsoft Windows 95 y versiones posteriores y las versiones de Windows NT 3.51 y versiones posteriores. Compatibilidad con Win32 de MFC incluye el subprocesamiento múltiple. Use la versión 1.5*x* si tiene que programar aplicaciones de 16 bits.

Esta serie de artículos presenta una amplia visión general del marco de la aplicación. También analiza los objetos principales que conforman la aplicación y cómo se crean. Entre los temas tratados en estos artículos son los siguientes:

- [El marco de trabajo](../mfc/framework-mfc.md).

- División del trabajo entre el marco de trabajo y el código, como se describe en [compilar en el marco](../mfc/building-on-the-framework.md).

- [La clase application](../mfc/cwinapp-the-application-class.md), que encapsula la funcionalidad del nivel de aplicación.

- Cómo [plantillas de documento](../mfc/document-templates-and-the-document-view-creation-process.md) crear y administrar documentos y sus vistas asociadas y ventanas de marco.

- Clase [CWnd](../mfc/window-objects.md), la clase base de la raíz de todas las ventanas.

- [Objetos gráficos](../mfc/graphic-objects.md), como lápices y pinceles.

Otras partes de framework se incluyen:

- [Window (objetos): información general](../mfc/window-objects.md)

- [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)

- [CObject, la clase Base raíz en MFC](../mfc/using-cobject.md)

- [Arquitectura documento/vista](../mfc/document-view-architecture.md)

- [Cuadros de diálogo](../mfc/dialog-boxes.md)

- [Controles](../mfc/controls-mfc.md)

- [Barras de control](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Administración de memoria](../mfc/memory-management.md)

     Además de proporcionar una ventaja de escribir aplicaciones para el sistema operativo de Windows, MFC también facilita mucho más fáciles de escribir aplicaciones que utilizan específicamente vinculación e incrustación de la tecnología OLE. Puede realizar la aplicación OLE visual de edición de contenedor, un servidor de edición visual OLE o ambos, y puede agregar automatización para que otras aplicaciones pueden usar los objetos de la aplicación o incluso controlarlo de forma remota.

- [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

     El kit de desarrollo de control OLE (CDK) ahora está totalmente integrado con el marco de trabajo. Esta serie de artículos proporciona información general sobre desarrollo de controles ActiveX con MFC. (Los controles ActiveX anteriormente eran conocidos como controles OLE).

- [Programación de la base de datos](../data/data-access-programming-mfc-atl.md)

     MFC también proporciona dos conjuntos de clases de base de datos que simplifican la escritura de acceso a datos de aplicaciones. Utilizando las clases de base de datos ODBC, puede conectarse a bases de datos a través de un controlador de Open Database Connectivity (ODBC), seleccionar los registros de las tablas y mostrar información del registro en un formulario en pantalla. Utilizando las clases de objeto de acceso a datos (DAO), puede trabajar con bases de datos a través del motor de base de datos Microsoft Jet o los orígenes de datos externos de (que no sean de Jet), incluidos los orígenes de datos ODBC.

     Además, MFC está totalmente habilitado para escribir aplicaciones que utilizan Unicode y juegos de caracteres multibyte (MBCS), juegos de caracteres de específicamente de doble byte (DBCS).

Para obtener una guía general para la documentación de MFC, vea [temas generales de MFC](../mfc/general-mfc-topics.md).

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)

