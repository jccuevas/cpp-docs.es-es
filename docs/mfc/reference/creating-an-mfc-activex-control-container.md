---
title: Crear un contenedor de controles ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 27f229a23595d4842a77409a3cedc7a57aa43e6c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079436"
---
# <a name="creating-an-mfc-activex-control-container"></a>Crear un contenedor de controles ActiveX MFC

Un contenedor de controles ActiveX es un programa primario que proporciona el entorno para que se ejecute un control ActiveX (anteriormente OLE). Puede crear una aplicación capaz de contener controles ActiveX con o sin MFC, pero es mucho más fácil hacerlo con MFC.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](../activex-controls.md).

La creación de un programa contenedor MFC mediante el [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md) permite tener acceso a las numerosas características de controles ActiveX y automatización que implementan las clases MFC y ActiveX. Estas características incluyen la edición visual, la automatización, la creación de archivos compuestos y la compatibilidad con los controles. Las opciones de edición visual del Asistente para aplicaciones MFC que admite el programa principal incluyen la creación de un contenedor, un pequeño servidor, un servidor completo y un programa que sea un contenedor y un servidor.

- **Nueva aplicación MFC**. Para crear un nuevo programa MFC que incluya automatización, edición visual, archivos compuestos o compatibilidad de control, use el Asistente para aplicaciones MFC y elija las opciones de automatización adecuadas.

- **Aplicación MFC existente**. Si va a agregar la contención de controles a una aplicación MFC existente, vea [contenedores de controles OLE: habilitar manualmente la contención de controles OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Para crear un contenedor de ActiveX para cualquiera de los siguientes tipos de aplicaciones

1. [Contenedores](../../mfc/containers.md)

1. [Edición visual](../../mfc/ole-mfc.md)

1. [Controles ActiveX MFC](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Consulte también

[Tipos de proyectos de C++ en Visual Studio](../../build/reference/visual-cpp-project-types.md)
