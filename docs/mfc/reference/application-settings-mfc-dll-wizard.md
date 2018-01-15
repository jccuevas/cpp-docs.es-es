---
title: "Configuración de la aplicación, Asistente para archivos DLL de MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.dll.appset
dev_langs: C++
helpviewer_keywords: MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1851460d5cf9deb8a803b13ec75d92c45c03e607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-mfc-dll-wizard"></a>Configuración de la aplicación, Asistente para archivos DLL de MFC
Utilice esta página del Asistente para la DLL de MFC para diseñar y agregar características básicas a un nuevo proyecto DLL de MFC.  
  
## <a name="dll-type"></a>Tipo de archivo DLL  
 Seleccione el tipo de archivo DLL que desee crear.  
  
 **DLL de MFC regular mediante compartido DLL de MFC**  
 Seleccione esta opción para vincular la biblioteca MFC con el programa como un archivo DLL compartido. Con esta opción, no se puede compartir objetos MFC entre el archivo DLL y la aplicación que realiza la llamada. El programa realiza llamadas a la biblioteca MFC en tiempo de ejecución. Esta opción reduce los requisitos de disco y memoria del programa si se compone de varios archivos ejecutables que utilizan la biblioteca MFC. Programas de Win32 y MFC pueden llamar a funciones en el archivo DLL. Debe redistribuir la DLL de MFC con este tipo de proyecto.  
  
 **Vincula estáticamente regular DLL de MFC con MFC**  
 Seleccione esta opción para vincular estáticamente el programa a la biblioteca MFC en tiempo de compilación. Programas de Win32 y MFC pueden llamar a funciones en el archivo DLL. Aunque esta opción aumenta el tamaño del programa, no es necesario redistribuir la DLL de MFC con este tipo de proyecto. No se puede compartir objetos MFC entre el archivo DLL y la aplicación que realiza la llamada.  
  
 **Archivo DLL de extensión MFC**  
 Seleccione esta opción si desea que el programa para realizar llamadas a la biblioteca MFC en tiempo de ejecución, y si desea compartir objetos MFC entre el archivo DLL y la aplicación que realiza la llamada. Esta opción reduce los requisitos de disco y memoria del programa, si se compone de varios archivos ejecutables que utilizan la biblioteca MFC. Sólo los programas MFC pueden llamar a funciones en el archivo DLL. Debe redistribuir la DLL de MFC con este tipo de proyecto.  
  
## <a name="additional-features"></a>Características adicionales  
 Seleccione si la DLL de MFC debe admitir la automatización y si deben admitir Windows sockets.  
  
 **Automatización**  
 Seleccione **automatización** para permitir que el programa manipular objetos implementados en otro programa. Seleccionar **automatización** también expone el programa a otros clientes de automatización. Vea [automatización](../../mfc/automation.md) para obtener más información.  
  
 **Sockets de Windows**  
 Seleccione esta opción para indicar que el programa compatible con Windows sockets. Windows sockets permite escribir programas que se comunican a través de redes TCP/IP.  
  
 Cuando la DLL de MFC con Windows sockets se crea con compatibilidad, [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) inicializa admite para los sockets y el archivo de encabezado MFC StdAfx.h incluye AfxSock.h.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md)   
 [Creación de un proyecto DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md)

