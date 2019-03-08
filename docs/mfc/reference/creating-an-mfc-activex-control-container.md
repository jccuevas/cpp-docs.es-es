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
ms.openlocfilehash: f0d5fe419375535ab8c52378b9005df88634e99a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275901"
---
# <a name="creating-an-mfc-activex-control-container"></a>Crear un contenedor de controles ActiveX MFC

Un contenedor de controles ActiveX es un programa primario que proporciona el entorno para un control ActiveX (anteriormente OLE) ejecutar. Puede crear una aplicación capaz de contener controles ActiveX con o sin MFC, pero resulta mucho más sencillo realizar con MFC.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](../activex-controls.md).

Creación de un programa de un contenedor MFC mediante el [MFC Application Wizard](../../mfc/reference/mfc-application-wizard.md) le permite acceder a muchas características de los controles ActiveX y automatización que se implementan mediante las clases MFC y ActiveX. Estas características incluyen la edición visual, automatización, la creación de archivos compuestos y soporte técnico para los controles. Las opciones de edición visuales de Asistente para aplicaciones MFC que admitirá el programa principal incluyen la creación de un contenedor, un miniservidor, un servidor completo y un programa que es un contenedor y un servidor.

- **Nueva aplicación MFC**. Para crear un nuevo programa MFC que incluye la automatización, edición visual, archivos compuestos o compatibilidad con controles, utilice el Asistente para aplicaciones MFC y elija las opciones de automatización.

- **Aplicación MFC existente**. Si va a agregar la contención de controles a una aplicación MFC existente, vea [contenedores de controles ActiveX: Habilitar manualmente la contención de controles OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Para crear un contenedor de ActiveX para cualquiera de los siguientes tipos de aplicaciones

1. [Contenedores](../../mfc/containers.md)

1. [Edición Visual](../../mfc/ole-mfc.md)

1. [Controles ActiveX MFC](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Vea también

[Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)
