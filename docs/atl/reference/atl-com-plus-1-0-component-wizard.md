---
title: Asistente para componentes ATL COM+ 1.0
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: d5c0c0c8edb6b698d3d8f50736121d987af98492
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321688"
---
# <a name="atl-com-10-component-wizard"></a>Asistente para componentes ATL COM+ 1.0

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Use este asistente para agregar un objeto al proyecto que admita servicios COM+ 1.0, incluidas las transacciones.

Puede especificar si el objeto admite interfaces duales y Automation. También puede indicar la compatibilidad con la interfaz de la información de error, el control de objetos mejorado, las transacciones y la puesta en cola de mensajes asincrónicos.

## <a name="remarks"></a>Observaciones

A partir de Visual Studio 2008, el script de registro producido por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la opción para **registrar componentes para todos los usuarios** del Asistente para ATL.

## <a name="names"></a>nombres

Especifique los nombres para el objeto, la interfaz y las clases que se van a agregar al proyecto. Excepto en el caso de **Nombre corto**, el resto de los cuadros se pueden editar independientemente de los demás. Si cambia el texto para **Nombre corto**, el cambio se refleja en los nombres del resto de los cuadros de esta página. Si cambia el nombre **Coclase** en la sección de COM, el cambio se refleja en los cuadros **Tipo** y **ProgID**, pero el nombre **Interfaz** no cambia. Este comportamiento de nomenclatura se ha diseñado para facilitarle la identificación de todos los nombres a medida que desarrolla su control.

- **Nombre corto**

   Especifica un nombre abreviado para el objeto. El nombre que proporciona determina los nombres `Class` y `Coclass`, los nombres archivo **.cpp** y archivo **.h**, el nombre **Interfaz**, los nombres **Tipo** y **ProgID**, a menos que cambie esos campos individualmente.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Clase**

   Establece el nombre de la clase que se va a crear. Este nombre se basa en el que se proporcione en **Nombre corto**, precedido de "C", el prefijo típico para un nombre de clase.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Con atributos**

   Indica si el objeto usa atributos. Si agrega un objeto a un proyecto ATL con atributos, esta opción estará activada y no se podrá cambiar. Es decir, solo puede agregar objetos con atributos a un proyecto creado con compatibilidad con atributos.

   Si selecciona esta opción para un proyecto ATL sin compatibilidad con atributos, el asistente le pide que especifique si desea agregar dicha compatibilidad al proyecto.

   Cualquier objeto que agregue después de establecer esta opción se designará como atributos de forma predeterminada (la casilla de verificación está seleccionada). Puede borrar esta casilla para agregar un objeto que no usa atributos.

   Consulte [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad COM del objeto.

- **Coclase**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.

> [!NOTE]
> Si crea su proyecto mediante atributos o indica en esta página del asistente que el componente COM+ 1.0 usa atributos, no puede cambiar esta opción porque ATL no incluye el atributo `coclass`.

- **Tipo**

   Establece la descripción del objeto que aparecerá en el Registro.

- **Interfaz**

   Establece la interfaz que crea para el objeto. Esta interfaz contiene sus métodos personalizados.

- **Progid**

   Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto.

::: moniker-end

## <a name="see-also"></a>Consulte también

[Componente COM+ 1.0 ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
