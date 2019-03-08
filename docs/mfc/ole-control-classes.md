---
title: Clases de controles OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 86470c3e3e66d6aee2ce532570cea096641d2c1d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304566"
---
# <a name="ole-control-classes"></a>Clases de controles OLE

Estas son las clases principales que usa al escribir controles OLE. El `COleControlModule` clase en un módulo de control OLE es como la [CWinApp](../mfc/reference/cwinapp-class.md) clase en una aplicación. Cada módulo implementa uno o varios controles OLE; Estos controles se representan mediante `COleControl` objetos. Estos controles comunican con sus contenedores con `CConnectionPoint` objetos.

El `CPictureHolder` y `CFontHolder` clases encapsulan las interfaces COM para imágenes y fuentes, mientras que el `COlePropertyPage` y `CPropExchange` clases le ayudarán a implementar páginas de propiedades y persistencia de la propiedad para el control.

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
Reemplaza el `CWinApp` clase para el módulo de control OLE. Derivar de la `COleControlModule` clase para desarrollar un objeto de módulo de control OLE. Proporciona funciones miembro para inicializar el módulo del control OLE.

[COleControl](../mfc/reference/colecontrol-class.md)<br/>
Derivar de la `COleControl` clase para desarrollar un control OLE. Deriva `CWnd`, esta clase hereda toda la funcionalidad de un objeto de ventana de Windows más funcionalidad específicas de OLE adicional, como la activación de eventos y la capacidad para admitir los métodos y propiedades.

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
La `CConnectionPoint` clase define un tipo especial de interfaz que se utiliza para comunicarse con otros objetos OLE, denominados punto de conexión. Un punto de conexión implementa una interfaz de salida que es capaz de iniciar acciones en otros objetos, como la activación de eventos y notificaciones de cambio.

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
Encapsula la funcionalidad de un objeto de imagen de Windows y el `IPicture` COM de la interfaz; usado para implementar la propiedad de imagen personalizada de un control OLE.

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
Encapsula la funcionalidad de un objeto de fuente de Windows y el `IFont` COM de la interfaz; usado para implementar la propiedad Font estándar de un control OLE.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Muestra las propiedades de OLE controlan en una interfaz gráfica, similar a un cuadro de diálogo.

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
Admite la implementación de persistencia de la propiedad para controles OLE. Análoga a [CDataExchange](../mfc/reference/cdataexchange-class.md) para cuadros de diálogo.

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
Toma un moniker, o una representación de cadena que puede convertir en un moniker y lo enlaza sincrónicamente en el flujo para el que el moniker es un nombre.

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
Funciona de forma similar a `CMonikerFile`; sin embargo, enlaza el moniker de forma asincrónica en la secuencia para que el moniker es un nombre.

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
Implementa una propiedad de control OLE transferida de forma asincrónica y almacenada en memoria caché en un archivo de memoria.

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
Permite a un documento activo recibir comandos que se originan en la interfaz de usuario de su contenedor (por ejemplo, FileNew, abrir, imprimir y así sucesivamente) y un contenedor recibir comandos que se originan en la interfaz de usuario del documento activo.

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
Funciona con las matrices de tipo y dimensión arbitrarios.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
