---
title: 'Controles ActiveX MFC: Temas avanzados'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: e0daabf3d236eb7038f22c54ea76d616baf613a0
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095998"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Controles ActiveX MFC: Temas avanzados

En este artículo se tratan temas avanzados relacionados con el desarrollo de controles ActiveX. Entre ellas se incluyen las siguientes:

- [Usar clases de base de datos en controles ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementar una propiedad parametrizada](#_core_implementing_a_parameterized_property)

- [Control de errores en el control ActiveX](#_core_handling_errors_in_your_activex_control)

- [Controlar claves especiales en el control](#_core_handling_special_keys_in_your_control)

- [Obtener acceso a los controles de cuadro de diálogo no visibles en tiempo de ejecución](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a>Usar clases de base de datos en controles ActiveX

Dado que las clases de controles ActiveX forman parte de la biblioteca de clases, puede aplicar los mismos procedimientos y reglas para usar las clases de base de datos en una aplicación MFC estándar para desarrollar controles ActiveX que utilicen las clases de base de datos MFC.

Para obtener información general sobre las clases de base de datos MFC, vea [clases de bases de datos MFC (DAO y ODBC)](../data/mfc-database-classes-odbc-and-dao.md). En este artículo se presentan las clases ODBC de MFC y las clases DAO de MFC y se indica a más detalles sobre cualquiera de ellos.

> [!NOTE]
>   DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta. Los asistentes C++ y el entorno visual no admiten DAO (aunque las clases DAO están incluidas y todavía se pueden utilizar). Microsoft recomienda que use [plantillas de OLE DB](../data/oledb/ole-db-programming.md) u [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para proyectos nuevos. Solo se debe utilizar DAO en el mantenimiento de las aplicaciones existentes.

##  <a name="_core_implementing_a_parameterized_property"></a>Implementar una propiedad parametrizada

Una propiedad parametrizada (a veces denominada matriz de propiedades) es un método para exponer una colección homogénea de valores como una única propiedad del control. Por ejemplo, puede usar una propiedad con parámetros para exponer una matriz o un diccionario como una propiedad. En Visual Basic, se tiene acceso a esta propiedad mediante la notación de matriz:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Use el Asistente para agregar propiedades para implementar una propiedad parametrizada. El Asistente para agregar propiedades implementa la propiedad agregando un par de funciones Get/Set que permiten al usuario del control obtener acceso a la propiedad mediante la notación anterior o de la manera estándar.

De forma similar a los métodos y las propiedades, las propiedades parametrizadas también tienen un límite en el número de parámetros permitidos. En el caso de las propiedades con parámetros, el límite es de 15 parámetros (con un parámetro reservado para almacenar el valor de propiedad).

En el procedimiento siguiente se agrega una propiedad parametrizada denominada array, a la que se puede tener acceso como una matriz bidimensional de enteros.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Para agregar una propiedad parametrizada mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

1. En el cuadro **nombre de propiedad** , `Array`escriba.

1. En el cuadro **tipo de propiedad** , seleccione **Short**.

1. Para tipo de **implementación** , haga clic en **métodos Get/Set**.

1. En los cuadros **obtener función** y **establecer función** , escriba nombres únicos para las funciones Get y set o acepte los nombres predeterminados.

9. Agregue un parámetro, denominado *Row* (tipo *Short*), mediante los controles **nombre de parámetro** y tipo de **parámetro** .

10. Agregue un segundo parámetro llamado *Column* (tipo *Short*).

11. Haga clic en **Finalizar**

### <a name="changes-made-by-the-add-property-wizard"></a>Cambios realizados por el Asistente para agregar propiedades

Cuando se agrega una propiedad personalizada, el Asistente para agregar propiedades realiza cambios en el encabezado de clase de control (. H) y la implementación (. CPP).

Las líneas siguientes se agregan a la clase control. H archivo:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Este código declara dos funciones llamadas `GetArray` y `SetArray` que permiten al usuario solicitar una fila y una columna específicas al obtener acceso a la propiedad.

Además, el Asistente para agregar propiedades agrega las líneas siguientes al mapa de envío de controles, que se encuentra en la implementación de la clase de control (. CPP):

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Por último, las implementaciones de `GetArray` las `SetArray` funciones y se agregan al final de. Archivo CPP. En la mayoría de los casos, modificará la función get para devolver el valor de la propiedad. La función set normalmente contendrá código que debe ejecutarse, ya sea antes o después de la modificación de la propiedad.

Para que esta propiedad sea útil, puede declarar una variable miembro de matriz bidimensional en la clase de control, de tipo **Short**, para almacenar los valores de la propiedad parametrizada. Después, puede modificar la función get para devolver el valor almacenado en la fila y la columna apropiadas, como se indica en los parámetros, y modificar la función set para actualizar el valor al que hacen referencia los parámetros de fila y columna.

##  <a name="_core_handling_errors_in_your_activex_control"></a>Control de errores en el control ActiveX

Si se producen condiciones de error en el control, es posible que tenga que notificar el error al contenedor de control. Hay dos métodos para informar de errores, en función de la situación en la que se produce el error. Si el error se produce en una función get o set de una propiedad, o dentro de la implementación de un método de automatización OLE, el control debe llamar a [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror), que indica al usuario del control que se ha producido un error. Si el error se produce en cualquier otro momento, el control debe llamar a [COleControl:: FireError (](../mfc/reference/colecontrol-class.md#fireerror), que desencadena un evento de error bursátil.

Para indicar el tipo de error que se ha producido, el control debe pasar un código de `ThrowError` error `FireError`a o. Un código de error es un código de estado OLE, que tiene un valor de 32 bits. Cuando sea posible, elija un código de error del conjunto estándar de códigos definido en OLECTL. Archivo de encabezado H. En la tabla siguiente se resumen estos códigos.

### <a name="activex-control-error-codes"></a>Códigos de error de controles ActiveX

|Error|DESCRIPCIÓN|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Llamada de función no válida|
|CTL_E_OVERFLOW|Desbordamiento|
|CTL_E_OUTOFMEMORY|Memoria agotada|
|CTL_E_DIVISIONBYZERO|División por cero|
|CTL_E_OUTOFSTRINGSPACE|Espacio de cadena insuficiente|
|CTL_E_OUTOFSTACKSPACE|Espacio de pila insuficiente|
|CTL_E_BADFILENAMEORNUMBER|Número o nombre de archivo incorrecto|
|CTL_E_FILENOTFOUND|No se encontró el archivo|
|CTL_E_BADFILEMODE|Modo de archivo incorrecto|
|CTL_E_FILEALREADYOPEN|Archivo ya abierto|
|CTL_E_DEVICEIOERROR|Error de E/S del dispositivo|
|CTL_E_FILEALREADYEXISTS|El archivo ya existe|
|CTL_E_BADRECORDLENGTH|Longitud de registro incorrecta|
|CTL_E_DISKFULL|Disco lleno|
|CTL_E_BADRECORDNUMBER|Número de registro incorrecto|
|CTL_E_BADFILENAME|Nombre de archivo incorrecto|
|CTL_E_TOOMANYFILES|Demasiados archivos|
|CTL_E_DEVICEUNAVAILABLE|Dispositivo no disponible|
|CTL_E_PERMISSIONDENIED|Permiso denegado|
|CTL_E_DISKNOTREADY|Disco no preparado|
|CTL_E_PATHFILEACCESSERROR|Error de acceso a la ruta/archivo|
|CTL_E_PATHNOTFOUND|No se encuentra la ruta de acceso|
|CTL_E_INVALIDPATTERNSTRING|Cadena de patrón no válida|
|CTL_E_INVALIDUSEOFNULL|Uso no válido de NULL|
|CTL_E_INVALIDFILEFORMAT|Formato de archivo no válido|
|CTL_E_INVALIDPROPERTYVALUE|Valor de propiedad no válido|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Índice de matriz de propiedad no válido|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|No se admite Set en tiempo de ejecución|
|CTL_E_SETNOTSUPPORTED|No se admite Set (propiedad de solo lectura).|
|CTL_E_NEEDPROPERTYARRAYINDEX|Se necesita un índice de matriz de propiedades|
|CTL_E_SETNOTPERMITTED|No se permite establecer|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|No se admite Get en tiempo de ejecución.|
|CTL_E_GETNOTSUPPORTED|No se admite Get (propiedad de solo escritura)|
|CTL_E_PROPERTYNOTFOUND|Propiedad no encontrada|
|CTL_E_INVALIDCLIPBOARDFORMAT|Formato de Portapapeles no válido|
|CTL_E_INVALIDPICTURE|Imagen no válida|
|CTL_E_PRINTERERROR|Error en la impresora|
|CTL_E_CANTSAVEFILETOTEMP|No se puede guardar el archivo en TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|No se encuentra el texto de la búsqueda|
|CTL_E_REPLACEMENTSTOOLONG|Los reemplazos son demasiado largos|

Si es necesario, use la macro CUSTOM_CTL_SCODE para definir un código de error personalizado para una condición que no esté incluida en uno de los códigos estándar. El parámetro de esta macro debe ser un entero comprendido entre 1000 y 32767, ambos incluidos. Por ejemplo:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Si va a crear un control ActiveX para reemplazar un control VBX existente, defina los códigos de error del control ActiveX con los mismos valores numéricos que usa el control VBX para asegurarse de que los códigos de error son compatibles.

##  <a name="_core_handling_special_keys_in_your_control"></a>Controlar claves especiales en el control

En algunos casos, puede que desee controlar ciertas combinaciones de teclas de una forma especial. por ejemplo, inserte una nueva línea cuando se presiona la tecla entrar en un control de cuadro de texto multilínea o se desplaza entre un grupo de controles de edición cuando se presiona un identificador de tecla direccional.

Si la clase base del control ActiveX es `COleControl`, puede invalidar [CWnd::P retranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage) para controlar los mensajes antes de que el contenedor los procese. Al usar esta técnica, devuelva siempre **true** si controla el mensaje en la invalidación `PreTranslateMessage`de.

En el ejemplo de código siguiente se muestra una posible manera de controlar los mensajes relacionados con las claves direccionales.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Para obtener más información sobre cómo controlar las interfaces de teclado de un control ActiveX, vea la documentación del SDK de ActiveX.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Obtener acceso a los controles de cuadro de diálogo no visibles en tiempo de ejecución

Puede crear controles de cuadro de diálogo que no tienen interfaz de usuario y son invisibles en tiempo de ejecución. Si agrega un control ActiveX invisible en tiempo de ejecución a un cuadro de diálogo y utiliza [CWnd:: GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) para tener acceso al control, el control no funcionará correctamente. En su lugar, debe utilizar una de las técnicas siguientes para obtener un objeto que represente el control:

- Mediante el Asistente para agregar variables miembro, seleccione **variable de control** y, a continuación, seleccione el identificador del control. Escriba un nombre de variable de miembro y seleccione la clase contenedora del control como el **tipo de control**.

     -o bien-

- Declare una variable local y una subclase como el elemento de cuadro de diálogo. Inserte código similar al siguiente (`CMyCtrl` es la clase contenedora, IDC_MYCTRL1 es el identificador del control):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
