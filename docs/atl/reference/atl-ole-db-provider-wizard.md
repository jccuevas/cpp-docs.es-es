---
title: Asistente para proveedores OLE DB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 91384d6c61368ee56ed303622e5c1bdfad09bd8a
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706961"
---
# <a name="atl-ole-db-provider-wizard"></a>Asistente para proveedores OLE DB ATL

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro producido por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la opción para **registrar componentes para todos los usuarios** del Asistente para ATL.

En la siguiente tabla se describen las opciones del Asistente para proveedores OLE DB ATL:

- **Nombre corto**

   Escriba el nombre corto del proveedor que se va a crear. Los otros cuadros de edición del asistente se rellenarán automáticamente en función de lo que escriba aquí. Puede editar los otros cuadros de nombre si lo desea.

- **Coclase**

   Nombre de la coclase. El nombre de ProgID cambiará para coincidir con este nombre.

- **Con atributos**

   Esta opción especifica si el asistente creará clases de proveedor mediante atributos o declaraciones de plantilla. Al seleccionar esta opción, el asistente usa atributos en lugar de declaraciones de plantilla (esta es la opción predeterminada si creó un proyecto con atributos). Al borrar esta opción, el asistente usa declaraciones de plantilla en lugar de atributos (esta es la opción predeterminada si creó un proyecto sin atributos).

   Si selecciona esta opción tras crear un proyecto sin atributos, el asistente le advierte de que el proyecto se convertirá en un proyecto con atributos y le pregunta si desea continuar.

- **ProgID**

   El identificador de programación o ProgID es una cadena de texto que puede utilizar la aplicación en lugar de un GUID. El nombre de ProgID tiene la forma *Projectname.Coclassname*.

- **Versión**

   Número de versión del proveedor. El valor predeterminado es 1.

- **Clase DataSource**

   Nombre de la clase de origen de datos, cuya forma es C*Shortname*Source.

- **Archivo .h de DataSource**

   Archivo de encabezado para la clase de origen de datos. Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente.

- **Clase de sesión**

   Nombre de la clase de sesión, cuya forma es C*Shortname*Session.

- **Archivo .h de sesión**

   Archivo de encabezado para la clase de sesión. Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente.

- **Clase de comando**

   Nombre de la clase de comando, cuya forma es C*Shortname*Command.

- **Archivo .h de comando**

   Archivo de encabezado para la clase de comando. Este nombre no se puede editar y depende del nombre del archivo de encabezado del conjunto de filas.

- **Clase de conjunto de filas**

   Nombre de la clase de conjunto de filas, cuya forma es C*Shortname*Rowset.

- **Archivo .h de conjunto de filas**

   Archivo de encabezado para la clase de conjunto de filas. Puede editar este nombre de archivo o seleccionar un archivo de encabezado existente.

- **Archivo .cpp de conjunto de filas**

   Archivo de implementación del proveedor. Puede editar este nombre de archivo o seleccionar un archivo de implementación existente.

::: moniker-end

## <a name="see-also"></a>Vea también

[Agregar un proveedor OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-provider.md)
