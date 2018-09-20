---
title: Detalles de compatibilidad con ATL agregan por el Asistente para ATL | Microsoft Docs
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
ms.openlocfilehash: efa96037139e61e16b752b45617bb8a3c54be993
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442154"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Información detallada sobre la compatibilidad agregada por el Asistente para ATL

Cuando se [agregar compatibilidad con ATL a un ejecutable MFC o una DLL existente](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C++ hace las siguientes modificaciones en el proyecto MFC existente (en este ejemplo, el proyecto se denomina `MFCEXE`):

- Se agregan dos nuevos archivos (un archivo .idl y un archivo .rgs usado para registrar el servidor).

- En los archivos de encabezado e implementación de aplicación principal (Mfcexe.h y Mfcexe.cpp), una nueva clase (derivada de `CAtlMFCModule`) se agrega. Además de la nueva clase, se agrega código para `InitInstance` para el registro. También se agrega código para el `ExitInstance` función para revocar el objeto de clase. En el archivo de encabezado, por último, se incluyen dos nuevos archivos de encabezado (Initguid.h y Mfcexe_i.c) en el archivo de implementación, declarar e inicializar los nuevos GUID para el `CAtlMFCModule`-clase derivada.

- Para registrar el servidor correctamente, se agrega una entrada para el nuevo archivo .rgs al archivo de recursos del proyecto.

## <a name="notes-for-dll-projects"></a>Notas para los proyectos DLL

Cuando se agrega compatibilidad con ATL a un proyecto de DLL de MFC, verá algunas diferencias. Se agrega código para el `DLLRegisterServer` y `DLLUnregisterServer` funciones para registrar y anular el registro de la DLL. También se agrega código para [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) y [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Vea también

[Compatibilidad con ATL en un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función Virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
