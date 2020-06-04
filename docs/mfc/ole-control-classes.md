---
title: Clases de controles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 47c28520d592c4bd49ab6cb40edbb2f5ddf59846
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447648"
---
# <a name="ole-control-classes"></a>Clases de controles OLE

Estas son las clases principales que se usan al escribir controles OLE. La clase `COleControlModule` en un módulo de control OLE es como la clase [CWinApp](../mfc/reference/cwinapp-class.md) en una aplicación. Cada módulo implementa uno o más controles OLE; Estos controles se representan mediante objetos `COleControl`. Estos controles se comunican con sus contenedores mediante `CConnectionPoint` objetos.

Las clases `CPictureHolder` y `CFontHolder` encapsulan interfaces COM para imágenes y fuentes, mientras que las clases `COlePropertyPage` y `CPropExchange` ayudan a implementar páginas de propiedades y persistencia de propiedades para el control.

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
Reemplaza la clase `CWinApp` del módulo de control OLE. Derive de la clase `COleControlModule` para desarrollar un objeto de módulo de control OLE. Proporciona funciones miembro para inicializar el módulo del control OLE.

[COleControl](../mfc/reference/colecontrol-class.md)<br/>
Derive de la clase `COleControl` para desarrollar un control OLE. Derivada de `CWnd`, esta clase hereda toda la funcionalidad de un objeto de ventana de Windows más funcionalidad adicional específica de OLE, como el desencadenamiento de eventos y la capacidad de admitir métodos y propiedades.

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
La clase `CConnectionPoint` define un tipo especial de interfaz que se utiliza para comunicarse con otros objetos OLE, denominado punto de conexión. Un punto de conexión implementa una interfaz de salida que puede iniciar acciones en otros objetos, como desencadenar eventos y notificaciones de cambios.

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
Encapsula la funcionalidad de un objeto de imagen de Windows y la interfaz COM de `IPicture`; se usa para implementar la propiedad de imagen personalizada de un control OLE.

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
Encapsula la funcionalidad de un objeto de fuente de Windows y la interfaz COM de `IFont`; se usa para implementar la propiedad Font estándar de un control OLE.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Muestra las propiedades de un control OLE en una interfaz gráfica, similar a un cuadro de diálogo.

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
Admite la implementación de la persistencia de propiedad para los controles OLE. Análogo a [CDataExchange (](../mfc/reference/cdataexchange-class.md) para los cuadros de diálogo.

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
Toma un moniker o una representación de cadena que puede realizar en un moniker y lo enlaza de forma sincrónica a la secuencia para la que el moniker es un nombre.

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
Funciona de forma similar a `CMonikerFile`; sin embargo, enlaza el moniker de forma asincrónica a la secuencia para la que el moniker es un nombre.

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
Implementa una propiedad de control OLE transferida de forma asincrónica y almacenada en memoria caché en un archivo de memoria.

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
Permite que un documento activo reciba comandos que se originan en la interfaz de usuario de su contenedor (como archivonuevo, apertura, impresión, etc.) y permite que un contenedor reciba comandos que se originan en la interfaz de usuario del documento activo.

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
Funciona con matrices de tipo y dimensión arbitrarios.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
