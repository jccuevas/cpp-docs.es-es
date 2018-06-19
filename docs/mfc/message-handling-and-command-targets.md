---
title: Destinos de comando y control de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7184a6e8df67dfd220173c42bfa3e0580bd2cd3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349472"
---
# <a name="message-handling-and-command-targets"></a>Control de mensajes y destinos de comando
La interfaz de envío de comandos `IOleCommandTarget` define un mecanismo sencillo y extensible para consultar y ejecutar comandos. Este mecanismo es más sencillo que de automatización `IDispatch` porque se basa completamente en un conjunto estándar de comandos; comandos no suelen tienen argumentos, y no está implicada ninguna información de tipo (seguridad de tipos se reduce para argumentos del comando).  
  
 En el diseño de interfaz de envío de comandos, cada comando pertenece a un grupo de comandos"" propio identificado con un **GUID**. Por lo tanto, cualquiera puede definir un grupo nuevo y definir todos los comandos dentro de ese grupo sin necesidad de coordinar con Microsoft o cualquier otro proveedor. (Esto es esencialmente el mismo tipo de definición como un **dispinterface** más **DISPID** en automatización. Hay superposición en este caso, aunque este mecanismo de enrutamiento de comandos es solo para el enrutamiento de comandos y no para secuencias de comandos o para la programación a gran escala como identificadores de automatización.)  
  
 `IOleCommandTarget` controla los siguientes escenarios:  
  
-   Cuando un objeto está activado, sólo se muestran generalmente las barras de herramientas del objeto y las barras de herramientas del objeto pueden tener botones para algunos de los comandos del contenedor como in situ **impresión**, **vista previa de impresión**,  **Guardar**, `New`, **Zoom**y otros. (Activación en contexto estándares recomienda que los objetos quiten estos botones de sus barras de herramientas, o en menos deshabiliten. Este diseño permite que estos comandos estén habilitados y se enruten al controlador correcto.) Actualmente, no hay ningún mecanismo para el objeto que se va a enviar estos comandos para el contenedor.  
  
-   Cuando un documento activo está incrustado en un contenedor de documentos activos (por ejemplo, Cuaderno de Office), el contenedor que tenga que enviar comandos tales **impresión**, **Configurar página**, **propiedades**y otros en el documento activo independiente.  
  
 Este sencillo enrutamiento de comandos podría controlarse mediante los estándares de automatización existentes y `IDispatch`. Sin embargo, la sobrecarga implicada en una `IDispatch` es superior al que es necesario en este caso, por lo que `IOleCommandTarget` proporciona un medio más sencillo para lograr los mismos fines:  
  
```  
interface IOleCommandTarget : IUnknown  
    {  
    HRESULT QueryStatus(  
        [in] GUID *pguidCmdGroup,  
        [in] ULONG cCmds,  
        [in,out][size_is(cCmds)] OLECMD *prgCmds,  
        [in,out] OLECMDTEXT *pCmdText);  
    HRESULT Exec(  
        [in] GUID *pguidCmdGroup,  
        [in] DWORD nCmdID,  
        [in] DWORD nCmdExecOpt,  
        [in] VARIANTARG *pvaIn,  
        [in,out] VARIANTARG *pvaOut);  
    }  
```  
  
 El `QueryStatus` este método comprueba si un determinado conjunto de comandos, el conjunto que se identifican con un **GUID**, se admite. Esta llamada rellena una matriz de **OLECMD** valores (estructuras) con la lista admitida de comandos, así como devolver el texto que describe el nombre de un comando o información de estado. Cuando el llamador desea invocar un comando, puede pasar el comando (y el conjunto **GUID**) a **Exec** junto con opciones y argumentos, recibir un valor devuelto.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de documentos activos](../mfc/active-document-containers.md)

