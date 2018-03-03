---
title: Asistente para objetos simples ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbefa4a8036802599dd97f31d57f18204fd6104f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-simple-object-wizard"></a>Asistente para objetos simples ATL
Este asistente inserta en el proyecto un objeto COM mínima. Utilice esta página del Asistente para especificar los nombres que identifican los archivos para el objeto y su funcionalidad COM y la clase de C++.  
  
 Use la [opciones](../../atl/reference/options-atl-simple-object-wizard.md) admite la página de este asistente para especificar el modelo de subprocesamiento del objeto, la agregación y si admite interfaces duales y la automatización. También puede indicar la compatibilidad para la interfaz de información de errores, puntos de conexión, compatibilidad con Internet Explorer y el cálculo de referencias de subprocesamiento libre.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la **registrar componente para todos los usuarios** opción del Asistente para ATL.  
  
## <a name="names"></a>Nombres  
 Especifique los nombres de objeto, interfaz y clases que se agrega al proyecto. Excepto para **nombre corto**, todos los demás cuadros pueden modificarse independientemente de las otras. Si cambia el texto para **nombre corto**, el cambio se reflejará en los nombres de todos los demás cuadros de esta página. Si cambia la **coclase** nombre en la sección COM, el cambio se refleja en el **tipo** y **ProgID** cuadros, pero la **interfaz** nombre no cambia. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables automáticamente a medida que desarrolla el control.  
  
> [!NOTE]
>  **Coclase** es editable en sólo los proyectos sin atributos. Si su proyecto tiene atributos, no se puede editar **coclase**.  
  
## <a name="c"></a>C++  
 Proporciona información sobre la clase de C++ creada para el objeto.  
  
 **Nombre corto**  
 Establece el nombre abreviado para el objeto. El nombre que utilice determinará la `Class` y **coclase** nombres, el **archivo .cpp** y **archivo .h** nombres, el **interfaz**nombre, el **tipo** nombres y la **ProgID**, a menos que cambie estos campos individualmente.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar la declaración de clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **Clase**  
 Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar a la implementación de la clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **El atributo**  
 Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no están disponibles para cambiar. Es decir, puede agregar solo los objetos con atributos a un proyecto creado con el soporte técnico de atributo.  
  
 Puede agregar un objeto con atributos solo a un proyecto ATL que utiliza atributos. Si selecciona esta opción para un proyecto ATL que no tiene compatibilidad atributo, el asistente le pide que especifique si desea agregar compatibilidad con atributos al proyecto.  
  
 De forma predeterminada, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.  
  
 Vea [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.  
  
## <a name="com"></a>COM  
 Proporciona información acerca de la funcionalidad de COM para el objeto.  
  
 **(Coclase)**  
 Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si se indican en esta página del asistente que el objeto utiliza atributos, no se puede cambiar esta opción, ya que ATL no incluye el `coclass` atributo.  
  
 **Type**  
 Establece la descripción del objeto que va a aparecer en el registro  
  
 **Interface**  
 Establece la interfaz que se crea para el objeto. Esta interfaz contiene los métodos personalizados.  
  
 **Id. de programa**  
 Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Objeto Simple ATL](../../atl/reference/adding-an-atl-simple-object.md)

