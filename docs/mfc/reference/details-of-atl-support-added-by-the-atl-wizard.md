---
title: Detalles de compatibilidad con ATL agregados por el Asistente para ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.atl.support
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ffe43c33e4b371f6d5dcf5dc7da327b11328af7
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121384"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Información detallada sobre la compatibilidad agregada por el Asistente para ATL
Cuando se [agregar compatibilidad con ATL a un ejecutable MFC o archivo DLL existente](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C++ hace las siguientes modificaciones en el proyecto MFC existente (en este ejemplo, el proyecto se denomina `MFCEXE`):  
  
-   Se agregan dos nuevos archivos (un archivo .idl y un archivo .rgs, usado para registrar el servidor).  
  
-   En los archivos de encabezado e implementación de aplicación principal (Mfcexe.h y Mfcexe.cpp), una nueva clase (derivado de `CAtlMFCModule`) se agrega. Además de la nueva clase, se agrega código a `InitInstance` para el registro. También se agrega código para el `ExitInstance` función para revocar el objeto de clase. En el archivo de encabezado, por último, se incluyen dos nuevos archivos de encabezado (Initguid.h y Mfcexe_i.c) en el archivo de implementación, declarar e inicializar el nuevo GUID para el `CAtlMFCModule`-clase derivada.  
  
-   Para registrar el servidor correctamente, se agrega una entrada para el nuevo archivo .rgs al archivo de recursos del proyecto.  
  
## <a name="notes-for-dll-projects"></a>Notas para los proyectos de archivos DLL  
 Cuando se agrega compatibilidad con ATL a un proyecto de DLL de MFC, verá algunas diferencias. Se agrega código a la `DLLRegisterServer` y `DLLUnregisterServer` funciones para registrar y anular el registro del archivo DLL. También se agrega código al [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) y [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con ATL en un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Adición de un controlador de mensajes MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
