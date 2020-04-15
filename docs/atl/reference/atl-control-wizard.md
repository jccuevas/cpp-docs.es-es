---
title: Asistente para controles ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321696"
---
# <a name="atl-control-wizard"></a>Asistente para controles ATL

Inserta en un proyecto ATL (o un proyecto MFC con compatibilidad con ATL) un control ATL. Puede utilizar este asistente para insertar uno de los tres tipos de controles:

- Control estándar

- Control compuesto

- Control DHTML

Además, puede especificar un control mínimo, quitando las interfaces de la lista [Interfaces,](../../atl/reference/interfaces-atl-control-wizard.md) que se proporcionan como valores predeterminados para que los controles se abran en la mayoría de los contenedores. Puede establecer las interfaces que desea que se admitan para el control en la página **Interfaces** del asistente.

## <a name="remarks"></a>Observaciones

El script de registro generado por este asistente registrará sus componentes COM en HKEY_CURRENT_USER en lugar de HKEY_LOCAL_MACHINE. Para modificar este comportamiento, establezca la opción para **registrar componentes para todos los usuarios** del Asistente para ATL.

## <a name="names"></a>nombres

Especifique los nombres para el objeto, la interfaz y las clases que se van a agregar al proyecto. A excepción de **Nombre corto**, todas las demás cajas se pueden cambiar de forma independiente. Si cambia el texto para **Nombre corto**, el cambio se refleja en los nombres del resto de los cuadros de esta página. Si cambia el nombre de **coclase** en la sección COM, el cambio se refleja en el cuadro **Tipo,** pero el nombre de la **interfaz** y **ProgID** no cambian. Este comportamiento de nomenclatura se ha diseñado para facilitarle la identificación de todos los nombres a medida que desarrolla su control.

> [!NOTE]
> **La coclase** solo se puede editar en controles no atribuidos. Si su proyecto tiene atributos, no podrá editar **Coclase**.

### <a name="c"></a>C++

Proporciona información para la clase de C++ creada para implementar el objeto.

- **Nombre corto**

   Especifica un nombre abreviado para el objeto. El nombre que proporcione determina los nombres de clase y **Coclase,** el archivo (. CPP y . H), el nombre de la interfaz y los nombres **de tipo,** a menos que cambie esos campos individualmente.

- **Clase**

   Establece el nombre de la clase que implementa el objeto. Este nombre se basa en el que se proporcione en **Nombre corto**, precedido de "C", el prefijo típico para un nombre de clase.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar**.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Con atributos**

   Indica si el objeto usa atributos. Si agrega un objeto a un proyecto ATL con atributos, esta opción estará activada y no se podrá cambiar. Es decir, solo puede agregar objetos con atributos a un proyecto creado con compatibilidad con atributos.

   Solo puede agregar un objeto con atributos a un proyecto ATL que usa atributos. Si selecciona esta opción para un proyecto ATL sin compatibilidad con atributos, el asistente le pide que especifique si desea agregar dicha compatibilidad al proyecto.

   De forma predeterminada, cualquier objeto que agregue una vez que establezca esta opción se designará como con atributos (la casilla estará activada). Puede borrar esta casilla para agregar un objeto que no usa atributos.

   Consulte [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

### <a name="com"></a>COM

Proporciona información sobre la funcionalidad COM del objeto.

- **Coclase**

   Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.

   > [!NOTE]
   > Si crea el proyecto mediante atributos, o si indica en esta página del asistente que el control utiliza atributos, no puede cambiar esta opción porque ATL no incluye el atributo **de coclase.**

- **Interfaz**

   Establece el nombre de la interfaz para el objeto. De forma predeterminada, un nombre de interfaz se antepone a "I".

- **Tipo**

   Establece la descripción del objeto que aparecerá en el Registro.

- **Progid**

   Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto. Este campo no se rellena automáticamente. Si no rellena manualmente este campo, es posible que el control no esté disponible para otras herramientas. Por ejemplo, los controles ActiveX `ProgID` que se generan sin a no están disponibles en el cuadro de diálogo **Insertar control ActiveX.** Para más información sobre el cuadro de diálogo, vea [Insertar control ActiveX (cuadro de diálogo)](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Consulte también

[Control ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Adición de funcionalidad al control compuesto](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Fundamentos de los objetos COM de ATL](../../atl/fundamentals-of-atl-com-objects.md)
