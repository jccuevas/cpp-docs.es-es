---
title: Asistente para componentes de páginas Active Server ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ASP components, creating in ATL
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: a78beeab663ef1b467cdec32ca51132e8134a9b2
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707050"
---
# <a name="atl-active-server-page-component-wizard"></a>Asistente para componentes de páginas Active Server ATL

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente inserta en el proyecto un componente de páginas Active Server (ASP). Microsoft Internet Information Services (IIS) usa componentes de ASP como parte de su arquitectura de desarrollo de páginas web mejorada.

Mediante este asistente, puede especificar el modelo de subprocesos del componente y su compatibilidad con la agregación. También puede indicar la compatibilidad con la interfaz de información de error, los puntos de conexión y la serialización de subproceso libre.

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro producido por este asistente registra sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la opción para **registrar componentes para todos los usuarios** del Asistente para ATL.

## <a name="names"></a>Nombres

Especifique los nombres para el objeto, la interfaz y las clases que se van a agregar al proyecto. Excepto en el caso de **Nombre corto**, el resto de los cuadros se pueden editar independientemente de los demás. Si cambia el texto para **Nombre corto**, el cambio se refleja en los nombres del resto de los cuadros de esta página.

Si cambia el nombre **Coclase** en la sección de COM, el cambio se refleja en los cuadros **Tipo** y **ProgID**, pero el nombre **Interfaz** no cambia. Este comportamiento de nomenclatura se ha diseñado para facilitarle la identificación de todos los nombres a medida que desarrolla su control.

### <a name="c"></a>C++

Proporciona información para la clase de C++ creada para el objeto.

- **Nombre corto**

   Establece el nombre raíz del objeto. El nombre que proporciona determina los nombres `Class` y **Coclase**, los nombres **Archivo .cpp** y **Archivo .h**, el nombre **Interfaz**, los nombres **Tipo** y **ProgID**, a menos que cambie esos campos individualmente.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Clase**

   Establece el nombre de la clase que se va a crear. Este nombre se basa en el que se proporcione en **Nombre corto**, precedido de "C", el prefijo típico para un nombre de clase.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Con atributos**

   Indica si el objeto usa atributos. Si agrega un objeto a un proyecto ATL con atributos, esta opción estará activada y no se podrá cambiar. Es decir, solo puede agregar objetos con atributos a un proyecto creado con compatibilidad con atributos.

   Si selecciona esta opción para un proyecto ATL sin compatibilidad con atributos, el asistente le pedirá que especifique si desea agregar dicha compatibilidad al proyecto.

   De forma predeterminada para los proyectos sin atributos, cualquier objeto que agregue una vez que establezca esta opción se designará como con atributos (la casilla estará activada). Puede borrar esta casilla para agregar un objeto que no usa atributos.

   Consulte [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad COM del objeto.

- **Coclass**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto. Si el proyecto o este objeto usa atributos, no podrá cambiar esta opción porque ATL no incluye el atributo **coclass**.

- **Type**

   Establece la descripción del objeto que aparecerá en el Registro para la coclase.

- **Interface**

   Establece la interfaz que crea para el objeto. Esta interfaz contiene sus métodos personalizados.

- **ProgID**

   Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto.

::: moniker-end

## <a name="see-also"></a>Vea también

[Agregar un componente de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
