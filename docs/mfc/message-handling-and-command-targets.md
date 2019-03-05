---
title: Control de mensajes y destinos de comando
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: 702cb96da13d6109c17a28e58c08a30af3f77fd4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302746"
---
# <a name="message-handling-and-command-targets"></a>Control de mensajes y destinos de comando

La interfaz de envío de comandos `IOleCommandTarget` define un mecanismo sencillo y extensible para consultar y ejecutar comandos. Este mecanismo es más sencillo que de Automation `IDispatch` porque se basa completamente en un conjunto estándar de comandos; los comandos no suelen tienen argumentos, y no está implicada ninguna información de tipo (seguridad de tipos se reduce para los argumentos de comando).

En el diseño de interfaz de envío de comandos, cada comando pertenece a un grupo de comandos"" que sí se identifica con un **GUID**. Por lo tanto, cualquier usuario puede definir un nuevo grupo y definir todos los comandos dentro de ese grupo sin necesidad de coordinar con Microsoft o cualquier otro proveedor. (Esto es esencialmente el mismo tipo de definición como un **dispinterface** plus **DISPID** en Automation. Hay superposición en este caso, aunque este mecanismo de enrutamiento de comandos es únicamente para el enrutamiento de comandos y no para scripting y programación a gran escala como identificadores de automatización).

`IOleCommandTarget` controla los siguientes escenarios:

- Cuando un objeto está activado, solo por lo general se muestran las barras de herramientas del objeto y las barras de herramientas del objeto pueden tener botones para algunos de los comandos del contenedor, como en el contexto **impresión**, **vista previa de impresión**,  **Guardar**, **New**, **Zoom**y otros. (Activación en contexto estándares recomienda que los objetos quiten esos botones de sus barras de herramientas o, al menos deshabiliten. Este diseño permite que estos comandos estén habilitados y se enruten al controlador correcto.) Actualmente, no hay ningún mecanismo para el objeto enviar estos comandos para el contenedor.

- Cuando un documento activo está incrustado en un contenedor de documentos activos (por ejemplo, el cuaderno de Office), el contenedor que deba enviar comandos tales **impresión**, **Configurar página**, **propiedades**y otros en el documento activo independiente.

Este enrutamiento de comandos simple podría controlarse a través de estándares de Automation existentes y `IDispatch`. Sin embargo, la sobrecarga implicada en una `IDispatch` es más que en este caso, es necesario para `IOleCommandTarget` proporciona una manera más sencilla para lograr los mismos fines:

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

El `QueryStatus` este método comprueba si un determinado conjunto de comandos, el conjunto que se identifican con un **GUID**, se admite. Esta llamada rellena una matriz de **OLECMD** valores (estructuras) con la lista de comandos, así como devolver el texto que describe el nombre de un comando o información de estado admitido. Cuando el llamador desea invocar un comando, puede pasar el comando (y el conjunto **GUID**) a `Exec` junto con las opciones y argumentos, obtener un valor devuelto.

## <a name="see-also"></a>Vea también

[Contenedores de documentos activos](../mfc/active-document-containers.md)
