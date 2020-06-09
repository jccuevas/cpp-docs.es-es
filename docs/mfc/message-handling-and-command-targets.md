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
ms.openlocfilehash: cbcbce1e476fef0d076f9c25b46b3166c1eb5935
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624348"
---
# <a name="message-handling-and-command-targets"></a>Control de mensajes y destinos de comando

La interfaz de envío de comandos `IOleCommandTarget` define un mecanismo sencillo y extensible para consultar y ejecutar comandos. Este mecanismo es más sencillo que la automatización `IDispatch` porque se basa completamente en un conjunto estándar de comandos; los comandos raramente tienen argumentos y no hay información de tipo implicada (la seguridad de tipos se reduce también para los argumentos de comando).

En el diseño de la interfaz de envío de comandos, cada comando pertenece a un "grupo de comandos" que se identifica con un **GUID**. Por lo tanto, cualquier usuario puede definir un nuevo grupo y definir todos los comandos de ese grupo sin necesidad de coordinarlo con Microsoft o con cualquier otro proveedor. (Este es esencialmente el mismo medio de definición que una **dispinterface** más los **DISPID** en Automation. Aquí se superponen, aunque este mecanismo de enrutamiento de comandos es solo para el enrutamiento de comandos y no para el scripting y la programación a gran escala como identificadores de automatización).

`IOleCommandTarget`controla los siguientes escenarios:

- Cuando un objeto está activado en contexto, solo se muestran las barras de herramientas del objeto y las barras de herramientas del objeto pueden tener botones para algunos de los comandos del contenedor como **Imprimir**, **vista previa de impresión**, **Guardar**, **nuevo**, **zoom**y otros. (Los estándares de activación en contexto recomiendan que los objetos quiten estos botones de las barras de herramientas o, al menos, deshabilitarlos. Este diseño permite que esos comandos se habiliten y se enruten al controlador correcto). Actualmente, no hay ningún mecanismo para que el objeto envíe estos comandos al contenedor.

- Cuando se inserta un documento activo en un contenedor de documentos activo (como el enlazador de Office), es posible que el contenedor necesite enviar comandos como **Imprimir**, **Configurar página**, **propiedades**y otros al documento activo contenido.

Este sencillo enrutamiento de comandos puede controlarse a través de los estándares de automatización existentes y `IDispatch` . Sin embargo, la sobrecarga que conlleva `IDispatch` es más de lo necesario aquí, por lo que `IOleCommandTarget` proporciona un medio más sencillo para lograr los mismos extremos:

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

`QueryStatus`En este caso, el método comprueba si se admite un conjunto determinado de comandos, el conjunto que se identifica con un **GUID**. Esta llamada rellena una matriz de valores **OLECMD** (estructuras) con la lista de comandos admitidos, así como la devolución de texto que describe el nombre de un comando o información de estado. Cuando el autor de la llamada desea invocar un comando, puede pasar el comando (y el **GUID**del conjunto) a `Exec` junto con las opciones y los argumentos, devolviendo un valor devuelto.

## <a name="see-also"></a>Consulte también

[Contenedores de documentos activos](active-document-containers.md)
