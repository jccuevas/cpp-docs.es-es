---
title: Información detallada sobre la compatibilidad agregada por el Asistente para ATL
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 10bafc9bd06ee94398f91d5af478a6e1cd7ca617
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108451"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Información detallada sobre la compatibilidad agregada por el Asistente para ATL

::: moniker range=">=vs-2019"

Al [Agregar compatibilidad con ATL a un archivo ejecutable o dll de MFC existente](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual Studio agrega un archivo de encabezado denominado *Framework. h* de forma predeterminada `#include` , `#define` que contiene las directivas de preprocesador y para habilitar el uso de ATL en el proyecto. No se agrega ningún archivo o clase adicional, como se hacía en versiones anteriores de Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Al [Agregar compatibilidad con ATL a un archivo ejecutable o dll de MFC existente](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual Studio realiza las siguientes modificaciones en el proyecto de MFC existente (en este ejemplo, se llama `MFCEXE`al proyecto):

- Se agregan dos nuevos archivos (un archivo. idl y un archivo. RGS, que se usa para registrar el servidor).

- En los archivos de encabezado y de implementación de la aplicación principal (Mfcexe. h y Mfcexe. cpp), se agrega `CAtlMFCModule`una nueva clase (derivada de). Además de la nueva clase, el código se agrega a `InitInstance` para el registro. También se agrega el código a `ExitInstance` la función para revocar el objeto de clase. En el archivo de encabezado, por último, se incluyen dos nuevos archivos de encabezado (Initguid. h y Mfcexe_i. c) en el archivo de implementación, declarando e inicializando `CAtlMFCModule`los nuevos GUID para la clase derivada de.

- Para registrar el servidor correctamente, se agrega una entrada para el nuevo archivo. RGS al archivo de recursos del proyecto.

::: moniker-end

## <a name="notes-for-dll-projects"></a>Notas para proyectos DLL

Al agregar compatibilidad con ATL a un proyecto DLL de MFC, verá algunas diferencias. El código se agrega a `DLLRegisterServer` las `DLLUnregisterServer` funciones y para registrar y anular el registro del archivo dll. También se agrega el código a [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) y [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Vea también

[Compatibilidad con ATL en un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigate-code-cpp.md)
