---
title: 'Controles ActiveX MFC: Temas avanzados | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99480a8d77aef1822034be100a03f73cfa9d1be0
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930009"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Controles ActiveX MFC: Temas avanzados
Este artículo tratan temas avanzados relacionados con el desarrollo de controles ActiveX. Se incluyen los siguientes:  
  
-   [Utilizar clases de base de datos en controles ActiveX](#_core_using_database_classes_in_activex_controls)  
  
-   [Implementar una propiedad con parámetros](#_core_implementing_a_parameterized_property)  
  
-   [Control de errores en el Control ActiveX](#_core_handling_errors_in_your_activex_control)  
  
-   [Trabajar con teclas especiales en el Control](#_core_handling_special_keys_in_your_control)  
  
-   [Obtener acceso a los controles de cuadro de diálogo que no son visibles en tiempo de ejecución](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a> Utilizar clases de base de datos en controles ActiveX  
 Dado que las clases de controles ActiveX forman parte de la biblioteca de clases, puede aplicar los mismos procedimientos y reglas de uso de las clases de base de datos en una aplicación de MFC estándar para desarrollar controles ActiveX que utilizan las clases de base de datos MFC.  
  
 Para obtener una descripción general de las clases de base de datos MFC, vea [clases de base de datos MFC (DAO y ODBC)](../data/mfc-database-classes-odbc-and-dao.md). El artículo detallan las clases ODBC de MFC y DAO de MFC, clases y le dirige a obtener más detalles sobre cualquiera.  
  
> [!NOTE]
>  El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice [plantillas OLE DB](../data/oledb/ole-db-programming.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para los nuevos proyectos. Solo debería utilizar DAO para mantener las aplicaciones existentes.  
  
##  <a name="_core_implementing_a_parameterized_property"></a> Implementar una propiedad con parámetros  
 Una propiedad con parámetros (también conocida como una matriz de propiedades) es un método para exponer una colección homogénea de valores como una única propiedad del control. Por ejemplo, puede utilizar una propiedad parametrizada para exponer una matriz o un diccionario como una propiedad. En Visual Basic, se tiene acceso a esta propiedad mediante la notación de matriz:  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 Usar al Asistente para agregar propiedades para implementar una propiedad con parámetros. El Asistente para agregar propiedades implementa la propiedad agregando un par de funciones Get/Set que permiten al usuario de control tener acceso a la propiedad mediante la notación anterior o en modo estándar.  
  
 Es similar a los métodos y propiedades, propiedades parametrizadas también tienen un límite al número de parámetros permitidos. En el caso de propiedades parametrizadas, el límite es de 15 parámetros (con un parámetro reservado para almacenar el valor de propiedad).  
  
 El siguiente procedimiento agrega una propiedad con parámetros, denominada matriz, que puede tener acceso como una matriz bidimensional de enteros.  
  
#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Para agregar una propiedad con parámetros mediante el Asistente para agregar propiedades  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
5.  En el **nombre de la propiedad** , escriba `Array`.  
  
6.  En el **tipo de propiedad** cuadro, seleccione **corto**.  
  
7.  Para **implementación** tipo, haga clic en **métodos Get/Set**.  
  
8.  En el **función Get** y **función Set** cuadros, escriba nombres únicos para sus funciones Get y Set o acepte los nombres predeterminados.  
  
9. Agregue un parámetro, denominado *fila* (tipo *corto*), usando la **nombre de parámetro** y **tipo de parámetro** controles.  
  
10. Agregue un segundo parámetro denominado *columna* (tipo *corto*).  
  
11. Haga clic en **Finalizar**.  
  
### <a name="changes-made-by-the-add-property-wizard"></a>Cambios realizados por el Asistente para agregar propiedades  
 Cuando se agrega una propiedad personalizada, el Asistente para agregar propiedades realiza cambios en los archivos de encabezado (. (H) y la implementación (. Archivos CPP).  
  
 Las líneas siguientes se agregan a la clase de control. Archivo H:  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]  
  
 Este código declara dos funciones denominadas `GetArray` y `SetArray` que permiten al usuario a solicitar una fila y columna específicas al obtener acceso a la propiedad.  
  
 Además, el Asistente para agregar propiedades agrega las siguientes líneas al mapa de envíos de control, que se encuentra en la implementación de la clase de control (. Archivo CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 Por último, las implementaciones de la `GetArray` y `SetArray` funciones se agregan al final de la. Archivo CPP. En la mayoría de los casos, se modificará la función Get para devolver el valor de la propiedad. La función Set normalmente contiene código que se debe ejecutar antes o después de cambiar la propiedad.  
  
 Para que esta propiedad para que sea útil, podría declarar una variable de miembro de matriz bidimensional en la clase de tipo de control, **corto**, para almacenar valores para la propiedad con parámetros. A continuación, podría modificar la función Get para devolver el valor almacenado en la fila y columna apropiadas, tal como se indica por los parámetros y modificar la función de conjunto para actualizar el valor que se hace referencia a los parámetros de fila y columna.  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a> Control de errores en el Control ActiveX  
 Si se producen condiciones de error en el control, debe notificar el error al contenedor del control. Existen dos métodos para notificar errores, según la situación en la que se produce el error. Si el error se produce dentro de una propiedad Get o Set (función), o dentro de la implementación de un método de automatización OLE, el control debe llamar a [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror), que señala al usuario del control que se ha producido un error. Si el error se produce en cualquier otro momento, el control debe llamar a [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror), que desencadena un evento de Error estándar.  
  
 Para indicar el tipo de error que se ha producido, el control debe pasar un código de error a `ThrowError` o `FireError`. Un código de error es un código de estado OLE, que tiene un valor de 32 bits. Cuando sea posible, elija un código de error en el conjunto estándar de códigos definidos en el OLECTL. Archivo de encabezado de H. En la tabla siguiente se resume estos códigos.  
  
### <a name="activex-control-error-codes"></a>Códigos de Error del Control ActiveX  
  
|Error|Descripción|  
|-----------|-----------------|  
|CTL_E_ILLEGALFUNCTIONCALL|Llamada de función no válido|  
|CTL_E_OVERFLOW|Desbordamiento|  
|CTL_E_OUTOFMEMORY|Memoria agotada|  
|CTL_E_DIVISIONBYZERO|División por cero|  
|CTL_E_OUTOFSTRINGSPACE|Espacio de cadena|  
|CTL_E_OUTOFSTACKSPACE|Espacio de pila insuficiente|  
|CTL_E_BADFILENAMEORNUMBER|Número o nombre de archivo incorrecto|  
|CTL_E_FILENOTFOUND|No se encontró el archivo|  
|CTL_E_BADFILEMODE|Modo de archivo incorrecto|  
|CTL_E_FILEALREADYOPEN|Archivo ya abierto|  
|CTL_E_DEVICEIOERROR|Error de E/S del dispositivo|  
|CTL_E_FILEALREADYEXISTS|El archivo ya existe|  
|CTL_E_BADRECORDLENGTH|Longitud de registro incorrecta|  
|CTL_E_DISKFULL|Disco está lleno|  
|CTL_E_BADRECORDNUMBER|Número de registro incorrecto|  
|CTL_E_BADFILENAME|Nombre de archivo incorrecto|  
|CTL_E_TOOMANYFILES|Demasiados archivos|  
|CTL_E_DEVICEUNAVAILABLE|Dispositivo no disponible|  
|CTL_E_PERMISSIONDENIED|Permiso denegado|  
|CTL_E_DISKNOTREADY|Disco no preparado|  
|CTL_E_PATHFILEACCESSERROR|Error de acceso de archivo o ruta de acceso|  
|CTL_E_PATHNOTFOUND|No se encuentra la ruta de acceso|  
|CTL_E_INVALIDPATTERNSTRING|Cadena de patrón no válida|  
|CTL_E_INVALIDUSEOFNULL|Uso no válido de NULL|  
|CTL_E_INVALIDFILEFORMAT|Formato de archivo no válido|  
|CTL_E_INVALIDPROPERTYVALUE|Valor de propiedad no válido|  
|CTL_E_INVALIDPROPERTYARRAYINDEX|Índice de matriz de propiedades no válido|  
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
|CTL_E_CANTSAVEFILETOTEMP|No se puede guardar el archivo en TEMP.|  
|CTL_E_SEARCHTEXTNOTFOUND|No se encuentra el texto de la búsqueda|  
|CTL_E_REPLACEMENTSTOOLONG|Los reemplazos son demasiado largos|  
  
 Si es necesario, utilice la macro CUSTOM_CTL_SCODE para definir un código de error personalizado para una condición que no está cubierto por uno de los códigos estándares. El parámetro para esta macro debe ser un entero entre 1000 y 32767, ambos inclusive. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 Si va a crear un control ActiveX para reemplazar un control VBX existente, defina los códigos de error del control ActiveX con los mismos valores numéricos que utiliza el control VBX para asegurarse de que los códigos de error son compatibles.  
  
##  <a name="_core_handling_special_keys_in_your_control"></a> Trabajar con teclas especiales en el Control  
 En algunos casos puede que desee controlar ciertas combinaciones de teclas de una manera especial; Por ejemplo, insertar una nueva línea cuando se presiona la tecla ENTRAR en un texto multilínea control de cuadro o se muevan entre un grupo de edición cuando controla una direccional presionado el identificador de la clave.  
  
 Si la clase base del control ActiveX es `COleControl`, puede invalidar [CWnd:: PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) para controlar los mensajes antes de que el contenedor los procese. Cuando se utiliza esta técnica, siempre devuelven **TRUE** si controla el mensaje en el reemplazo de `PreTranslateMessage`.  
  
 En el ejemplo de código siguiente se muestra una posible manera de controlar los mensajes relacionados con las teclas de dirección.  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 Para obtener más información sobre cómo controlar las interfaces de teclado para un control ActiveX, vea la documentación de SDK de ActiveX.  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> Obtener acceso a los controles de cuadro de diálogo que no son visibles en tiempo de ejecución  
 Puede crear controles de cuadro de diálogo que no tienen ninguna interfaz de usuario y no son visibles en tiempo de ejecución. Si agrega un invisible en tiempo de ejecución control ActiveX en un cuadro de diálogo y utilizar [CWnd:: GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) para el control de acceso, el control no funcionará correctamente. En su lugar, debe usar una de las siguientes técnicas para obtener un objeto que representa el control:  
  
-   Con el miembro Asistente para agregar variables, seleccione **Control Variable** y, a continuación, seleccione el identificador. del control Escriba un nombre de variable de miembro y seleccione la clase del control contenedor como el **tipo de Control**.  
  
     O bien  
  
-   Declare una variable local y una subclase como el elemento de cuadro de diálogo. Inserte código similar al siguiente (`CMyCtrl` es la clase contenedora, IDC_MYCTRL1 es el identificador del control):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

