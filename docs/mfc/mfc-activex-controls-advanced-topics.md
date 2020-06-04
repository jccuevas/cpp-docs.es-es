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
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364637"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Controles ActiveX MFC: Temas avanzados

En este artículo se tratan temas avanzados relacionados con el desarrollo de controles ActiveX. Entre ellas se incluyen las siguientes:

- [Uso de clases de base de datos en controles ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementación de una propiedad parametrizada](#_core_implementing_a_parameterized_property)

- [Manejo de errores en el control ActiveX](#_core_handling_errors_in_your_activex_control)

- [Manejo de llaves especiales en el control](#_core_handling_special_keys_in_your_control)

- [Acceso a controles de cuadro de diálogo que son invisibles en tiempo de ejecución](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>Uso de clases de base de datos en controles ActiveX

Dado que las clases de control ActiveX forman parte de la biblioteca de clases, puede aplicar los mismos procedimientos y reglas para usar clases de base de datos en una aplicación MFC estándar para desarrollar controles ActiveX que usan las clases de base de datos MFC.

Para obtener información general sobre las clases de base de datos MFC, vea Clases de base de [datos MFC (DAO y ODBC).](../data/mfc-database-classes-odbc-and-dao.md) El artículo presenta las clases ODBC de MFC y las clases DAO de MFC y le indica más detalles sobre cualquiera de ellas.

> [!NOTE]
> DAO se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto. El entorno y los asistentes de Visual C++ no admiten DAO (aunque las clases DAO están incluidas y todavía puede usarlas). Microsoft recomienda usar [plantillas OLE DB](../data/oledb/ole-db-programming.md) u ODBC y [MFC](../data/odbc/odbc-and-mfc.md) para nuevos proyectos. Solo debe usar DAO para mantener las aplicaciones existentes.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>Implementación de una propiedad parametrizada

Una propiedad parametrizada (a veces denominada matriz de propiedades) es un método para exponer una colección homogénea de valores como una sola propiedad del control. Por ejemplo, puede usar una propiedad parametrizada para exponer una matriz o un diccionario como una propiedad. En Visual Basic, se tiene acceso a una propiedad de este tipo mediante la notación de matriz:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Utilice el Asistente para agregar propiedades para implementar una propiedad con parámetros. El Asistente para agregar propiedades implementa la propiedad agregando un par de funciones Get/Set que permiten al usuario del control tener acceso a la propiedad mediante la notación anterior o de forma estándar.

Al igual que los métodos y propiedades, las propiedades parametrizadas también tienen un límite en el número de parámetros permitidos. En el caso de las propiedades parametrizadas, el límite es de 15 parámetros (con un parámetro reservado para almacenar el valor de propiedad).

El siguiente procedimiento agrega una propiedad parametrizada, denominada Array, a la que se puede tener acceso como una matriz bidimensional de enteros.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Para agregar una propiedad parametrizada mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

1. En el cuadro Nombre `Array`de **propiedad,** escriba .

1. En el cuadro **Tipo de propiedad,** seleccione **short**.

1. En **Tipo de implementación,** haga clic en **Obtener/Establecer métodos**.

1. En los cuadros **Obtener función** y **Establecer función,** escriba nombres únicos para las funciones Get y Set o acepte los nombres predeterminados.

1. Agregue un parámetro, denominado *fila* (tipo *corto*), mediante los controles Nombre de **parámetro** y Tipo de **parámetro.**

1. Agregue un segundo parámetro denominado *columna* (tipo *short*).

1. Haga clic en **Finalizar**

### <a name="changes-made-by-the-add-property-wizard"></a>Cambios realizados por el Asistente para agregar propiedades

Al agregar una propiedad personalizada, el Asistente para agregar propiedades realiza cambios en el encabezado de la clase de control (. H) y la implementación (. CPP).

Las siguientes líneas se agregan a la clase de control . H archivo:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Este código declara dos `GetArray` `SetArray` funciones a las que se llama y que permiten al usuario solicitar una fila y columna específica al tener acceso a la propiedad.

Además, el Asistente para agregar propiedades agrega las siguientes líneas al mapa de distribución de control, ubicado en la implementación de la clase de control (. CPP) archivo:

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Por último, las `GetArray` implementaciones de las funciones y `SetArray` se agregan al final del archivo . Archivo CPP. En la mayoría de los casos, modificará la función Get para devolver el valor de la propiedad. La función Set normalmente contendrá código que se debe ejecutar, antes o después de que cambie la propiedad.

Para que esta propiedad sea útil, podría declarar una variable miembro de matriz bidimensional en la clase de control, de tipo **short**, para almacenar valores para la propiedad parametrizada. A continuación, puede modificar la función Get para devolver el valor almacenado en la fila y columna adecuadas, como se indica en los parámetros, y modificar la función Set para actualizar el valor al que hacen referencia los parámetros de fila y columna.

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>Manejo de errores en el control ActiveX

Si se producen condiciones de error en el control, es posible que deba notificar el error al contenedor de control. Existen dos métodos para notificar errores, dependiendo de la situación en la que se produzca el error. Si el error se produce dentro de una propiedad Get o Set función, o dentro de la implementación de un método de automatización OLE, el control debe llamar a [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), que indica al usuario del control que se ha producido un error. Si el error se produce en cualquier otro momento, el control debe llamar a [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), que desencadena un evento Error de stock.

Para indicar el tipo de error que se ha `ThrowError` producido, el control debe pasar un código de error a o `FireError`. Un código de error es un código de estado OLE, que tiene un valor de 32 bits. Cuando sea posible, elija un código de error del conjunto estándar de códigos definidos en OLECTL. Archivo de encabezado H. En la tabla siguiente se resumen estos códigos.

### <a name="activex-control-error-codes"></a>Códigos de error de control ActiveX

|Error|Descripción|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Llamada de función ilegal|
|CTL_E_OVERFLOW|Desbordamiento|
|CTL_E_OUTOFMEMORY|No hay memoria suficiente|
|CTL_E_DIVISIONBYZERO|División por cero|
|CTL_E_OUTOFSTRINGSPACE|Espacio de cadena insuficiente|
|CTL_E_OUTOFSTACKSPACE|Espacio de pila insuficiente|
|CTL_E_BADFILENAMEORNUMBER|Número o nombre de archivo incorrecto|
|CTL_E_FILENOTFOUND|Archivo no encontrado|
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
|CTL_E_INVALIDPROPERTYARRAYINDEX|Indice de matriz de propiedades no válido|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|No se admite Set en tiempo de ejecución|
|CTL_E_SETNOTSUPPORTED|No se admite Set (propiedad de solo lectura).|
|CTL_E_NEEDPROPERTYARRAYINDEX|Se necesita un índice de matriz de propiedades|
|CTL_E_SETNOTPERMITTED|No se permite establecer|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|No se admite Get en tiempo de ejecución.|
|CTL_E_GETNOTSUPPORTED|No se admite Get (propiedad de solo escritura)|
|CTL_E_PROPERTYNOTFOUND|Propiedad no encontrada|
|CTL_E_INVALIDCLIPBOARDFORMAT|Formato de portapapeles no válido|
|CTL_E_INVALIDPICTURE|Imagen no válida|
|CTL_E_PRINTERERROR|Error en la impresora|
|CTL_E_CANTSAVEFILETOTEMP|No se puede guardar el archivo en TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|No se encuentra el texto de la búsqueda|
|CTL_E_REPLACEMENTSTOOLONG|Los reemplazos son demasiado largos|

Si es necesario, utilice la macro CUSTOM_CTL_SCODE para definir un código de error personalizado para una condición que no esté cubierta por uno de los códigos estándar. El parámetro para esta macro debe ser un entero entre 1000 y 32767, ambos inclusive. Por ejemplo:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Si va a crear un control ActiveX para reemplazar un control VBX existente, defina los códigos de error de control ActiveX con los mismos valores numéricos que utiliza el control VBX para asegurarse de que los códigos de error son compatibles.

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>Manejo de llaves especiales en el control

En algunos casos es posible que desee manejar ciertas combinaciones de teclas de una manera especial; por ejemplo, inserte una nueva línea cuando se presione la tecla ENTRAR en un control de cuadro de texto de varias líneas o muévase entre un grupo de controles de edición cuando se presiona un identificador de tecla direccional.

Si la clase base del `COleControl`control ActiveX es , puede invalidar [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) para controlar los mensajes antes de que el contenedor los procese. Al usar esta técnica, devuelva siempre **TRUE** si `PreTranslateMessage`controla el mensaje en la invalidación de .

En el ejemplo de código siguiente se muestra una posible forma de controlar los mensajes relacionados con las claves direccionales.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Para obtener más información sobre el control de interfaces de teclado para un control ActiveX, consulte la documentación del SDK de ActiveX.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Acceso a controles de cuadro de diálogo que son invisibles en tiempo de ejecución

Puede crear controles de cuadro de diálogo que no tengan interfaz de usuario y sean invisibles en tiempo de ejecución. Si agrega un control ActiveX invisible en tiempo de ejecución a un cuadro de diálogo y usa [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) para tener acceso al control, el control no funcionará correctamente. En su lugar, debe utilizar una de las siguientes técnicas para obtener un objeto que represente el control:

- Mediante el Asistente para agregar variables miembro, seleccione Variable de **control** y, a continuación, seleccione el identificador del control. Escriba un nombre de variable miembro y seleccione la clase contenedora del control como Tipo de **control**.

     o bien

- Declare una variable local y una subclase como elemento de cuadro de diálogo. Insertar código similar al`CMyCtrl` siguiente ( es la clase contenedora, IDC_MYCTRL1 es el identificador del control):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
