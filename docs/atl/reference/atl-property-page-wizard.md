---
title: Asistente para páginas de propiedades ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: 5808a99d376ab3640c955156688d64bc0285e67e
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706989"
---
# <a name="atl-property-page-wizard"></a>Asistente para páginas de propiedades ATL

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente [agrega una página de propiedades a un proyecto ATL](../../atl/reference/adding-an-atl-property-page.md) o a un proyecto MFC con compatibilidad ATL. Una página de propiedades ATL proporciona una interfaz de usuario para establecer las propiedades (o llamar a los métodos) de uno o varios objetos COM.

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2008, el script de registro producido por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la opción para **registrar componentes para todos los usuarios** del Asistente para ATL.

## <a name="names"></a>Nombres

Especifique los nombres para el objeto, la interfaz y las clases que se van a agregar al proyecto. Excepto en el caso de **Nombre corto**, el resto de los cuadros se pueden editar de manera independiente. Si cambia el texto para **Nombre corto**, el cambio se reflejará en los nombres del resto de los cuadros de esta página. Si cambia el nombre **Coclase** en la sección de COM, el cambio se reflejará en los cuadros **Tipo** y **ProgID**. Este comportamiento de nomenclatura se ha diseñado para facilitarle la identificación de todos los nombres a medida que desarrolla su página de propiedades.

> [!NOTE]
>  **Coclase** solo se puede editar en proyectos sin atributos. Si su proyecto tiene atributos, no podrá editar **Coclase**.

### <a name="c"></a>C++

Proporciona información para la clase de C++ creada para implementar el objeto.

|||
|-|-|
|Término|Definición|
|**Nombre corto**|Especifica un nombre abreviado para el objeto. El nombre que proporciona determina los nombres de clase y **Coclase**, los nombres de archivo (**.cpp** y **.h**), el nombre **Tipo** y **ProgID**, a menos que cambie esos campos individualmente.|
|**Archivo .h**|Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.<br /><br /> El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.|
|**Clase**|Establece el nombre de la clase que implementa el objeto. Este nombre se basa en el que se proporcione en **Nombre corto**, precedido de "C", el prefijo típico para un nombre de clase.|
|**Archivo .cpp**|Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.<br /><br /> El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.|
|**Con atributos**|Indica si el objeto usa atributos. Si agrega un objeto a un proyecto ATL con atributos, esta opción estará activada y no se podrá cambiar. Es decir, solo puede agregar objetos con atributos a un proyecto creado con compatibilidad con atributos.<br /><br /> Solo puede agregar un objeto con atributos a un proyecto ATL que usa atributos. Si selecciona esta opción para un proyecto ATL sin compatibilidad con atributos, el asistente le pedirá que especifique si desea agregar dicha compatibilidad al proyecto.<br /><br /> De forma predeterminada, cualquier objeto que agregue una vez que establezca esta opción se designará como con atributos (la casilla estará activada). Puede borrar esta casilla para agregar un objeto que no usa atributos.<br /><br /> Consulte [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.|

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad COM del objeto.

- **Coclass**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.

   > [!NOTE]
   > Si crea su proyecto mediante atributos o indica en esta página del asistente que la página de propiedades usa atributos, no podrá cambiar esta opción porque ATL no incluye el atributo `coclass`.

- **Type**

   Establece la descripción del objeto que aparecerá en el Registro.

- **ProgID**

   Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto.

::: moniker-end

## <a name="see-also"></a>Vea también

[Opciones, Asistente para páginas de propiedades ATL](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)
