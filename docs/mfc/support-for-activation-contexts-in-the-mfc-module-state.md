---
title: Compatibilidad con los contextos de activación en el estado del módulo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: a2e5f56eeb323f1bd5f20c5920bbdbe4a658554d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306670"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Compatibilidad con los contextos de activación en el estado del módulo MFC

MFC crea un contexto de activación mediante un recurso de manifiesto proporcionado por el módulo de usuario. Para obtener más información sobre cómo se crean los contextos de activación, vea los temas siguientes:

- [Contextos de activación](/windows/desktop/SbsCs/activation-contexts)

- [Manifiestos de aplicación](/windows/desktop/SbsCs/application-manifests)

- [Manifiestos de ensamblado](/windows/desktop/SbsCs/assembly-manifests)

## <a name="remarks"></a>Comentarios

Al leer estos temas del SDK de Windows, tenga en cuenta que el mecanismo de contexto de activación de MFC se parece el contexto de activación de Windows SDK, excepto que MFC no utiliza la API del contexto de activación de Windows SDK.

Contexto de activación funciona en aplicaciones MFC, archivos DLL de usuario y archivos DLL de extensión MFC de las maneras siguientes:

- Aplicaciones de MFC usan 1 Id. de recurso para su recurso de manifiesto. En este caso, el MFC no crea su propio contexto de activación, pero usa el contexto de la aplicación predeterminada.

- Usuario archivos DLL MFC utiliza 2 Id. de recurso para su recurso de manifiesto. En este caso, MFC crea un contexto de activación para cada DLL de usuario, por lo que otro usuario los archivos DLL puede usar versiones diferentes de las mismas bibliotecas (por ejemplo, la biblioteca de controles comunes).

- Archivos DLL de extensión MFC se basan en sus aplicaciones de hospedaje o un usuario dll para establecer su contexto de activación.

Aunque se puede modificar el estado del contexto de activación con los procesos descritos en [mediante la API de contexto de activación](/windows/desktop/SbsCs/using-the-activation-context-api), mediante el mecanismo de contexto de activación de MFC puede ser útil al desarrollar arquitecturas para complementos basados en DLL donde no es fácil (o no es posible) para cambiar manualmente el estado de activación antes y después de las llamadas individuales a los complementos externos.

Se crea el contexto de activación en [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit). Se destruye en el `AFX_MODULE_STATE` destructor. Un identificador de contexto de activación se mantiene en `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` se describe en [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate).)

El [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) macro activa y desactiva el contexto de activación. `AFX_MANAGE_STATE` está habilitada para que las bibliotecas estáticas de MFC, así como archivos DLL de MFC, para permitir que el código MFC ejecutar en el contexto de activación correcto seleccionado por el archivo DLL de usuario.

## <a name="see-also"></a>Vea también

[Contextos de activación](/windows/desktop/SbsCs/activation-contexts)<br/>
[Manifiestos de aplicación](/windows/desktop/SbsCs/application-manifests)<br/>
[Manifiestos de ensamblado](/windows/desktop/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
