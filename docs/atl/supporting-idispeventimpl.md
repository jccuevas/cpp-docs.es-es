---
title: Admitir IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329322"
---
# <a name="supporting-idispeventimpl"></a>Admitir IDispEventImpl

La clase de plantilla [IDispEventImpl](../atl/reference/idispeventimpl-class.md) se puede utilizar para proporcionar compatibilidad con receptores de puntos de conexión en la clase ATL. Un receptor de punto de conexión permite a la clase controlar eventos desencadenados desde objetos COM externos. Estos receptores de punto de conexión se asignan con un mapa de receptores de eventos, proporcionado por la clase.

Para implementar correctamente un receptor de punto de conexión para la clase, se deben completar los pasos siguientes:

- Importar las bibliotecas de tipos para cada objeto externo

- Declarar `IDispEventImpl` las interfaces

- Declarar un mapa de receptor de eventos

- Aconsejar y desaconsejar los puntos de conexión

Los pasos necesarios para implementar un receptor de punto de conexión se realizan modificando solo el archivo de encabezado (.h) de la clase.

## <a name="importing-the-type-libraries"></a>Importación de las bibliotecas de tipos

Para cada objeto externo cuyos eventos desee controlar, debe importar la biblioteca de tipos. Este paso define los eventos que se pueden controlar y proporciona información que se utiliza al declarar el mapa del receptor de eventos. La directiva [#import](../preprocessor/hash-import-directive-cpp.md) se puede utilizar para lograr esto. Agregue las `#import` líneas de directiva necesarias para cada interfaz de envío que admita al archivo de encabezado (.h) de la clase.

En el ejemplo siguiente se importa la`MSCAL.Calendar.7`biblioteca de tipos de un servidor COM externo ( ):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> Debe tener una `#import` instrucción independiente para cada biblioteca de tipos externa que admita.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Declarar las interfaces IDispEventImpl

Ahora que ha importado las bibliotecas de tipos de cada `IDispEventImpl` interfaz de envío, debe declarar interfaces independientes para cada interfaz de envío externa. Modifique la declaración de `IDispEventImpl` la clase agregando una declaración de interfaz para cada objeto externo. Para obtener más información sobre los parámetros, vea [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

El código siguiente declara dos receptores `DCalendarEvents` de punto de conexión, para `CMyCompositCtrl2`la interfaz, para el objeto COM implementado por la clase:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Declarar un mapa de sumidero de eventos

Para que las notificaciones de eventos se controlen mediante la función adecuada, la clase debe enrutar cada evento a su controlador correcto. Esto se logra declarando un mapa de receptores de eventos.

ATL proporciona varias macros, [BEGIN_SINK_MAP,](reference/composite-control-macros.md#begin_sink_map) [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)y [SINK_ENTRY_EX,](reference/composite-control-macros.md#sink_entry_ex)que facilitan esta asignación. El formato estándar es el siguiente:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

En el ejemplo siguiente se declara un mapa de receptor de eventos con dos controladores de eventos:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

La implementación está casi completa. El último paso se refiere al asesoramiento y desasesoramiento de las interfaces externas.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Asesoramiento y desasesoramiento de las interfaces IDispEventImpl

El último paso es implementar un método que aconsejará (o desaconsejará) todos los puntos de conexión en los momentos adecuados. Este asesoramiento debe realizarse antes de que pueda tener lugar la comunicación entre los clientes externos y el objeto. Antes de que el objeto sea visible, se consulta cada interfaz de envío externa admitida por el objeto para las interfaces salientes. Se establece una conexión y se utiliza una referencia a la interfaz saliente para controlar los eventos del objeto. Este procedimiento se conoce como "asesoramiento".

Una vez que el objeto haya terminado con las interfaces externas, se debe notificar a las interfaces salientes que ya no las utiliza la clase. Este proceso se conoce como "desaconsejo".

Debido a la naturaleza única de los objetos COM, este procedimiento varía, en detalle y en ejecución, entre implementaciones. Estos detalles están fuera del ámbito de este tema y no se tratan.

## <a name="see-also"></a>Consulte también

[Fundamentos de los objetos COM de ATL](../atl/fundamentals-of-atl-com-objects.md)
