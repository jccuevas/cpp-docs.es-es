---
title: "Controles ActiveX MFC: Temas avanzados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FireError (método)"
  - "controles ActiveX en MFC, obtener acceso a controles de cuadro de diálogo invisible"
  - "controles ActiveX en MFC, temas avanzados"
  - "controles ActiveX en MFC, clases de base de datos"
  - "controles ActiveX en MFC, códigos de error"
  - "controles ActiveX en MFC, propiedades parametrizadas"
  - "controles ActiveX en MFC, teclas especiales"
  - "PreTranslateMessage (método)"
  - "ThrowError (método)"
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Temas avanzados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo cubre temas avanzados relacionados con desarrollar controles ActiveX.  Se incluyen los siguientes:  
  
-   [Utilizar clases de base de datos en Controles ActiveX](#_core_using_database_classes_in_activex_controls)  
  
-   [Implementar una propiedad de Parametrizada](#_core_implementing_a_parameterized_property)  
  
-   [Controlar errores en el control ActiveX se](#_core_handling_errors_in_your_activex_control)  
  
-   [Administrar claves especial en el Control](#_core_handling_special_keys_in_your_control)  
  
-   [El diálogo de acceso controla Que invisible en tiempo de ejecución](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a> Utilizar clases de base de datos en Controles ActiveX  
 Dado que las clases de control ActiveX forman parte de la biblioteca de clases, puede solicitar los mismos procedimientos y reglas utilizar clases de base de datos en una aplicación estándar de MFC a desarrollar controles ActiveX que utilizan las clases de base de datos MFC.  
  
 Para obtener información general sobre de las clases de base de datos de MFC, vea [Clases de base de datos MFC \(DAO y ODBC\)](../data/mfc-database-classes-odbc-and-dao.md).  El caso presenta las clases ODBC de MFC y las clases DAO de MFC y guía a más detalles en.  
  
> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda utilizar [Plantillas OLE DB](../data/oledb/ole-db-programming.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para nuevos proyectos.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
##  <a name="_core_implementing_a_parameterized_property"></a> Implementar una propiedad de Parametrizada  
 Una propiedad con parámetros \(denominada en ocasiones una matriz de propiedades\) es un método para exponer una colección homogénea de valores como una propiedad del control.  Por ejemplo, puede utilizar una propiedad con parámetros para exponer una matriz o un diccionario como una propiedad.  En Visual Basic, esta propiedad se usa la notación de matrices:  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/VisualBasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 Utilice el asistente para agregar propiedades para implementar una propiedad parametrizada.  El asistente para agregar implementa la propiedad agregando un par de funciones Get\/set que permiten al usuario del control tenga acceso a la propiedad mediante la notación anterior o en modo estándar.  
  
 Similar a los métodos y propiedades, propiedades parametrizadas también tienen un límite al número de parámetros permitidos.  En el caso de propiedades parametrizadas, el límite es 15 parámetros \(con un parámetro reservado para almacenar el valor de propiedad\).  
  
 El procedimiento siguiente se agrega una propiedad con parámetros, denominada Array, que puede tener acceso como matriz de enteros bidimensional.  
  
#### Para agregar una propiedad con parámetros mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
5.  En el cuadro de **Nombre de propiedad** , `Array`escrito.  
  
6.  En el cuadro de **Tipo de propiedad** , seleccione **corto**.  
  
7.  Para el tipo de **Implementación** , haga clic en **Get\/Set Methods**.  
  
8.  En los cuadros de **Get Function** y de **Establecer función** , nombres únicos escritos para las funciones get y set o aceptan los nombres predeterminados.  
  
9. Agregue un parámetro, denominado `row` \(tipo `short`\), utilizando los controles de **Nombre del parámetro** y de **Tipo de parámetro** .  
  
10. Agregue `column` denominado segundo parámetro \(tipo `short`\).  
  
11. Haga clic en **Finalizar**.  
  
### Cambios realizados por el asistente para agregar propiedades  
 Cuando se agrega una propiedad personalizada, el asistente para agregar realiza cambios en el encabezado de la clase control \(. H\) y los archivos de implementación \(.CPP\).  
  
 Las líneas siguientes se agregan a la clase de control. Archivo de h:  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_2.h)]  
  
 Este código declara dos funciones llamadas `GetArray` y `SetArray` que permiten al usuario solicitar una fila y una columna específicas para tener acceso a la propiedad.  
  
 Además, el asistente para agregar agregue las líneas siguientes al mapa de envío del control, ubicado en el archivo de implementación de la clase control \(.CPP\):  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 Finalmente, las implementaciones de `GetArray` y las funciones de `SetArray` se agregan al final del archivo de .CPP.  En la mayoría de los casos, modificará la función get para devolver el valor de la propiedad.  La función determinada contendrá normalmente el código que debe ejecutarse, antes o después de que la propiedad cambia.  
  
 Para que esta propiedad sea útil, puede declarar una variable miembro de la matriz bidimensional en la clase de control, de **corto**tipo, los valores almacenados para la propiedad parametrizada.  A continuación modificar la función get para devolver el valor almacenado en la fila y la columna adecuadas, como se indica en los parámetros, y modifica la función determinada para actualizar el valor hace referencia a los parámetros de fila y columna.  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a> Controlar errores en el control ActiveX se  
 Si las condiciones de error aparecen en el control, puede ser necesario notificar el error al contenedor del control.  Hay dos métodos para notificar errores, dependiendo de la situación en la que el error.  Si el error se produce dentro de una propiedad obtiene o establece la función, o dentro de la implementación de un método de automatización OLE, el control debe llamar a [COleControl::ThrowError](../Topic/COleControl::ThrowError.md), que señala al usuario del control que se ha producido un error a.  Si el error se produce en otro momento, el control debe llamar a [COleControl::FireError](../Topic/COleControl::FireError.md), que activa un evento Error común.  
  
 Para indicar el tipo de error que se ha producido, el control debe pasar un código de error a `ThrowError` o a `FireError`.  Un código de error es un código de estado OLE, que tiene un valor de 32 bits.  Cuando sea posible, elija un código de error del conjunto estándar de códigos definidos en el archivo de encabezado de OLECTL.H.  La tabla siguiente se resumen estos códigos.  
  
### Códigos de error de controles ActiveX  
  
|Error|Descripción|  
|-----------|-----------------|  
|**CTL\_E\_ILLEGALFUNCTIONCALL**|Llamada ilegal a una función|  
|**CTL\_E\_OVERFLOW**|Desbordamiento|  
|**CTL\_E\_OUTOFMEMORY**|Memoria insuficiente|  
|**CTL\_E\_DIVISIONBYZERO**|División por cero|  
|**CTL\_E\_OUTOFSTRINGSPACE**|Sin espacio de cadena|  
|**CTL\_E\_OUTOFSTACKSPACE**|Sin espacio de pila|  
|**CTL\_E\_BADFILENAMEORNUMBER**|Nombre de archivo incorrecto o número|  
|**CTL\_E\_FILENOTFOUND**|Archivo no encontrado|  
|**CTL\_E\_BADFILEMODE**|Modo de archivo incorrecto|  
|**CTL\_E\_FILEALREADYOPEN**|Archivo abierto|  
|**CTL\_E\_DEVICEIOERROR**|Error de E\/S de dispositivo|  
|**CTL\_E\_FILEALREADYEXISTS**|El archivo ya existe|  
|**CTL\_E\_BADRECORDLENGTH**|Longitud de registro errónea|  
|**CTL\_E\_DISKFULL**|Disco lleno|  
|**CTL\_E\_BADRECORDNUMBER**|Número de registros de error|  
|**CTL\_E\_BADFILENAME**|Nombre de archivo incorrecto|  
|**CTL\_E\_TOOMANYFILES**|Demasiados archivos|  
|**CTL\_E\_DEVICEUNAVAILABLE**|Dispositivo no disponibles|  
|**CTL\_E\_PERMISSIONDENIED**|Permiso denegado|  
|**CTL\_E\_DISKNOTREADY**|Disco no está listo|  
|**CTL\_E\_PATHFILEACCESSERROR**|Ruta\/al archivo|  
|**CTL\_E\_PATHNOTFOUND**|Ruta no encontrada|  
|**CTL\_E\_INVALIDPATTERNSTRING**|Cadena no válida del modelo|  
|**CTL\_E\_INVALIDUSEOFNULL**|Uso no válido de NULL|  
|**CTL\_E\_INVALIDFILEFORMAT**|Formato de archivo no válido|  
|**CTL\_E\_INVALIDPROPERTYVALUE**|Valor de propiedad no válido|  
|**CTL\_E\_INVALIDPROPERTYARRAYINDEX**|Índice no válido de la matriz de propiedades|  
|**CTL\_E\_SETNOTSUPPORTEDATRUNTIME**|Conjunto no compatible en tiempo de ejecución|  
|**CTL\_E\_SETNOTSUPPORTED**|Conjunto no compatible \(propiedad de sólo lectura\)|  
|**CTL\_E\_NEEDPROPERTYARRAYINDEX**|Índice de la matriz de propiedades de la necesidad|  
|**CTL\_E\_SETNOTPERMITTED**|Conjunto no permitido|  
|**CTL\_E\_GETNOTSUPPORTEDATRUNTIME**|Obtenga no compatible en tiempo de ejecución|  
|**CTL\_E\_GETNOTSUPPORTED**|Obtenga no compatible \(la propiedad de sólo escritura\)|  
|**CTL\_E\_PROPERTYNOTFOUND**|Propiedad no encontrada|  
|**CTL\_E\_INVALIDCLIPBOARDFORMAT**|Formato no válido del portapapeles|  
|**CTL\_E\_INVALIDPICTURE**|Imagen no válida|  
|**CTL\_E\_PRINTERERROR**|Error de impresora|  
|**CTL\_E\_CANTSAVEFILETOTEMP**|No puede guardar el archivo en TEMP|  
|**CTL\_E\_SEARCHTEXTNOTFOUND**|Busque el texto no encontrado|  
|**CTL\_E\_REPLACEMENTSTOOLONG**|Reemplazos demasiado largo|  
  
 Si es necesario, utilice la macro de **CUSTOM\_CTL\_SCODE** para definir un código de error personalizado para una condición que no está cubierto por uno de los códigos estándar.  El parámetro para esta macro debe ser un entero entre 1000 y 32767, ambos inclusive.  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 Si está creando un control ActiveX para reemplazar un control existente de VBX, defina los códigos de error de control ActiveX con los mismos valores numéricos que el control de VBX utiliza para garantizar que los códigos de error son compatibles.  
  
##  <a name="_core_handling_special_keys_in_your_control"></a> Administrar claves especial en el Control  
 Puede que en algunos casos para controlar ciertas combinaciones de presiones de tecla de una manera especial; por ejemplo, inserte una nueva línea cuando la tecla ENTRAR se clava un control o un movimiento de cuadro de texto de varias líneas entre un grupo de controles de edición cuando un Id. de clave direccional presionó.  
  
 Si la clase base de controles ActiveX es `COleControl`, puede reemplazar [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md) para controlar los mensajes antes de que el contenedor los procese.  Con esta técnica, **VERDADERO** siempre return si controla el mensaje en la invalidación de `PreTranslateMessage`.  
  
 El ejemplo de código siguiente se muestra una manera de administrar cualquier mensaje relacionado con teclas direccionales.  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 Para obtener más información sobre cómo administrar las interfaces de teclado para un control ActiveX, vea la documentación de ActiveX SDK.  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> Controles de acceso de diálogo ese invisible en tiempo de ejecución  
 Puede crear controles de cuadro de diálogo que no tienen interfaz de usuario y no son visibles en tiempo de ejecución.  Si agrega un no visible en el control ActiveX en tiempo de ejecución a un cuadro de diálogo y utiliza [CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md) para tener acceso al control, el control no funcionará correctamente.  En su lugar, debe usar una de las técnicas siguientes para obtener un objeto que representa el control:  
  
-   Mediante el asistente para agregar variables miembro, **Control Variable** seleccione y seleccione el identificador de control  Escriba un nombre de variable miembro y seleccione la clase contenedora de control como **Tipo de control**.  
  
     O bien  
  
-   Declare una variable local y conviértala subclases como elemento de diálogo.  Inserte el código similar al siguiente \(`CMyCtrl` es la clase contenedora, `IDC_MYCTRL1` es el identificador del control\):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)