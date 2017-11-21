---
title: "Compatibilidad con contextos de activación en el estado del módulo MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9a15941848a9e8d5bdf35dfebf273f7684fbb8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Compatibilidad con los contextos de activación en el estado del módulo MFC
MFC crea un contexto de activación con un recurso del manifiesto proporcionado por el módulo de usuario. Para obtener más información sobre cómo se crean los contextos de activación, vea los temas siguientes:  
  
-   [Contextos de activación](http://msdn.microsoft.com/library/aa374153)  
  
-   [Manifiestos de aplicación](http://msdn.microsoft.com/library/aa374191)  
  
-   [Manifiestos de ensamblado](http://msdn.microsoft.com/library/aa374219)  
  
## <a name="remarks"></a>Comentarios  
 Al leer estos temas del SDK de Windows, tenga en cuenta que el mecanismo de contexto de activación de MFC se parece el contexto de activación de Windows SDK salvo que MFC no utiliza la API de contexto de activación de Windows SDK.  
  
 Contexto de activación funciona en aplicaciones MFC, archivos DLL de usuario y archivos DLL de extensión MFC de las maneras siguientes:  
  
-   Aplicaciones de MFC utilizan identificador de recursos 1 para su recurso de manifiesto. En este caso, la MFC no crea su propio contexto de activación, pero usa el contexto de aplicación predeterminado.  
  
-   Usuario archivos DLL MFC utilice 2 Id. de recurso para el recurso del manifiesto. En este caso, MFC crea un contexto de activación para cada DLL de usuario, por lo que otro usuario dll puede usar distintas versiones de las mismas bibliotecas (por ejemplo, la biblioteca de controles comunes).  
  
-   Archivos DLL de extensión MFC se basan en sus aplicaciones de hospedaje o el usuario dll para establecer su contexto de activación.  
  
 Aunque se puede modificar el estado del contexto de activación con los procesos descritos en [mediante la API de contexto de activación](http://msdn.microsoft.com/library/aa376620), mediante el mecanismo de contexto de activación de MFC puede ser útil al desarrollar arquitecturas complemento basado en DLL donde no resulta fácil (o no es posible) para cambiar manualmente el estado de activación antes y después de las llamadas individuales a complementos externos.  
  
 Se crea el contexto de activación en [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit). Se destruye en el `AFX_MODULE_STATE` destructor. Un identificador de contexto de activación se mantiene en `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` se describe en [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate).)  
  
 El [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) macro activa y desactiva el contexto de activación. `AFX_MANAGE_STATE`se habilita para que bibliotecas estáticas de MFC, así como archivos DLL de MFC, para permitir que el código MFC ejecutar en el contexto de activación correcta seleccionado por el archivo DLL de usuario.  
  
## <a name="see-also"></a>Vea también  
 [Contextos de activación](http://msdn.microsoft.com/library/aa374153)   
 [Manifiestos de aplicación](http://msdn.microsoft.com/library/aa374191)   
 [Manifiestos de ensamblado](http://msdn.microsoft.com/library/aa374219)   
 [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)   
 [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)   
 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)

