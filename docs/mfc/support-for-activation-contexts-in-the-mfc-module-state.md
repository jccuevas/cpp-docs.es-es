---
title: Compatibilidad con los contextos de activación en el estado del módulo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: 296df3d2ecec74c5c9a7deef1617298d40243724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511434"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Compatibilidad con los contextos de activación en el estado del módulo MFC

MFC crea un contexto de activación mediante un recurso de manifiesto proporcionado por el módulo de usuario. Para obtener más información sobre cómo se crean los contextos de activación, vea los temas siguientes:

- [Contextos de activación](/windows/win32/SbsCs/activation-contexts)

- [Manifiestos de aplicación](/windows/win32/SbsCs/application-manifests)

- [Manifiestos de ensamblado](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>Comentarios

Al leer estos Windows SDK temas, tenga en cuenta que el mecanismo de contexto de activación de MFC es similar al contexto de activación Windows SDK, salvo que MFC no utiliza la API de contexto de activación de Windows SDK.

El contexto de activación funciona en las aplicaciones MFC, los archivos dll de usuario y los archivos dll de extensión de MFC de las siguientes maneras:

- Las aplicaciones MFC usan el identificador de recurso 1 para su recurso de manifiesto. En este caso, MFC no crea su propio contexto de activación, sino que usa el contexto de aplicación predeterminado.

- Los archivos dll de usuario de MFC usan el identificador de recurso 2 para su recurso de manifiesto. En este caso, MFC crea un contexto de activación para cada archivo DLL de usuario, por lo que los distintos archivos dll de usuario pueden usar versiones diferentes de las mismas bibliotecas (por ejemplo, la biblioteca de controles comunes).

- Los archivos dll de extensión de MFC dependen de las aplicaciones de hospedaje o de los archivos dll de usuario para establecer su contexto de activación.

Aunque el estado del contexto de activación se puede modificar con los procesos descritos en [uso de la API de contexto de activación](/windows/win32/SbsCs/using-the-activation-context-api), el uso del mecanismo de contexto de activación de MFC puede ser útil al desarrollar arquitecturas de complemento basadas en dll, donde no es fácil (o no es posible) para cambiar manualmente el estado de activación antes y después de las llamadas individuales a complementos externos.

El contexto de activación se crea en [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit). Se destruye en el `AFX_MODULE_STATE` destructor. Un identificador de contexto de activación se `AFX_MODULE_STATE`mantiene en. (`AFX_MODULE_STATE` se describe en [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)).

La macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) activa y desactiva el contexto de activación. `AFX_MANAGE_STATE`está habilitado para las bibliotecas estáticas de MFC, así como archivos dll de MFC, para permitir que el código MFC se ejecute en el contexto de activación adecuado seleccionado por el archivo DLL de usuario.

## <a name="see-also"></a>Vea también

[Contextos de activación](/windows/win32/SbsCs/activation-contexts)<br/>
[Manifiestos de aplicación](/windows/win32/SbsCs/application-manifests)<br/>
[Manifiestos de ensamblado](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
