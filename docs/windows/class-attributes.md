---
title: Atributos de clase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a2fe111028f952482dbd6b2eedebc157d39a9a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645180"
---
# <a name="class-attributes"></a>Atributos de clase
Los siguientes atributos se aplican a la [clase](../cpp/class-cpp.md) palabra clave de C++.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Indica que la clase admite agregación.|  
|[aggregates](../windows/aggregates.md)|Indica que un control agrega la clase de destino.|  
|[appobject](../windows/appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa .exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|  
|[case](../windows/case-cpp.md)|Puede usar con el [switch_type](../windows/switch-type.md) atributo en una unión.|  
|[coclass](../windows/coclass.md)|Crea un control ActiveX.|  
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Agrega una entrada de la interfaz a un mapa COM.|  
|[control](../windows/control.md)|Especifica que el tipo definido por el usuario es un control.|  
|[Personalizado](../windows/custom-cpp.md)|Le permite definir su propio atributo.|  
|[db_command](../windows/db-command.md)|Crea un comando OLE DB.|  
|[db_param](../windows/db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|  
|[db_source](../windows/db-source.md)|Crea una conexión a un origen de datos.|  
|[db_table](../windows/db-table.md)|Se abre una tabla de OLE DB.|  
|[default](../windows/default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|  
|[defaultvtable](../windows/defaultvtable.md)|Define una interfaz que la interfaz de vtable predeterminada para un control.|  
|[event_receiver](../windows/event-receiver.md)|Crea un receptor de eventos.|  
|[event_source](../windows/event-source.md)|Crea un origen de eventos.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el **ayuda** archivo.|  
|[helpfile](../windows/helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|  
|[hidden](../windows/hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|  
|[Implementa](../windows/implements-cpp.md)|Especifica las interfaces de envío que se ven obligadas a ser miembros de la coclase IDL.|  
|[implements_category](../windows/implements-category.md)|Especifica las categorías de componentes implementados para la clase.|  
|[módulo](../windows/module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|  
|[noncreatable](../windows/noncreatable.md)|Define un objeto que no pueden crearse instancias por sí mismo.|  
|[progid](../windows/progid.md)|Define el ProgID de un control.|  
|[registration_script](../windows/registration-script.md)|Ejecuta el script de registro especificado.|  
|[requestedit](../windows/requestedit.md)|Indica que la propiedad admite la `OnRequestEdit` notificación.|  
|[source](../windows/source-cpp.md)|Especifica las interfaces de origen del control de puntos de conexión en una clase. En una propiedad o método, el `source` atributo indica que el miembro devuelve un objeto o `VARIANT` que es un origen de eventos.|  
|[support_error_info](../windows/support-error-info.md)|Admite informes de errores para el objeto de destino.|  
|[Subprocesamiento](../windows/threading-cpp.md)|Especifica el modelo de subprocesos para un control.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
|[version](../windows/version-cpp.md)|Identifica una versión determinada entre varias versiones de una clase.|  
|[vi_progid](../windows/vi-progid.md)|Especifica una forma independiente de la versión de ProgID.|  
  
## <a name="see-also"></a>Vea también  
 [Atributos por uso](../windows/attributes-by-usage.md)