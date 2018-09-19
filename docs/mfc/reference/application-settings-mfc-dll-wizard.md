---
title: Configuración de la aplicación, Asistente para archivos DLL de MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04fcf796c7d08cc2733edbf23b66c591e07ec71a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704982"
---
# <a name="application-settings-mfc-dll-wizard"></a>Configuración de la aplicación, Asistente para archivos DLL de MFC
Utilice esta página del Asistente para la DLL de MFC para diseñar y agregar características básicas a un nuevo proyecto de DLL de MFC.  
  
## <a name="dll-type"></a>Tipo de archivo DLL  
 Seleccione el tipo de archivo DLL que desee crear.  
  
- **DLL de MFC regular mediante compartido DLL de MFC**

   Seleccione esta opción para vincular la biblioteca MFC con el programa como un archivo DLL compartido. Con esta opción, no se puede compartir objetos MFC entre el archivo DLL y la aplicación que realiza la llamada. El programa realiza llamadas a la biblioteca MFC en tiempo de ejecución. Esta opción reduce los requisitos de disco y memoria del programa si se compone de varios archivos ejecutables que utilizan la biblioteca MFC. Programas de Win32 y MFC pueden llamar a funciones en el archivo DLL. Debe redistribuir las DLL de MFC con este tipo de proyecto.  
  
- **MFC DLL con MFC vinculada estáticamente**

   Seleccione esta opción para vincular estáticamente el programa a la biblioteca MFC en tiempo de compilación. Programas de Win32 y MFC pueden llamar a funciones en el archivo DLL. Aunque esta opción aumenta el tamaño del programa, no es necesario redistribuir la DLL de MFC con este tipo de proyecto. No se puede compartir objetos MFC entre el archivo DLL y la aplicación que realiza la llamada.  
  
- **Archivo DLL de extensión MFC**

   Seleccione esta opción si desea que el programa para realizar llamadas a la biblioteca MFC en tiempo de ejecución, y si desea compartir objetos MFC entre el archivo DLL y la aplicación que realiza la llamada. Esta opción reduce los requisitos de disco y memoria de programa, si se compone de varios archivos ejecutables que utilizan la biblioteca MFC. Sólo los programas MFC pueden llamar a funciones en el archivo DLL. Debe redistribuir las DLL de MFC con este tipo de proyecto.  
  
## <a name="additional-features"></a>Características adicionales  

Seleccione si la DLL de MFC debe admitir la automatización y si deben admitir sockets de Windows.  
  
- **Automatización**

   Seleccione **automatización** para permitir que el programa manipular objetos implementados en otro programa. Seleccionar **automatización** también expone el programa a otros clientes de automatización. Consulte [automatización](../../mfc/automation.md) para obtener más información.  
  
- **Sockets de Windows**

   Seleccione esta opción para indicar que el programa admite sockets de Windows. Sockets de Windows le permiten escribir programas que se comunican a través de redes TCP/IP.  
  
   Cuando la DLL de MFC con Windows sockets se crea el soporte técnico, [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) inicializa la compatibilidad con sockets y el archivo de encabezado MFC StdAfx.h incluye AfxSock.h.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md)   
 [Creación de un proyecto DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md)

