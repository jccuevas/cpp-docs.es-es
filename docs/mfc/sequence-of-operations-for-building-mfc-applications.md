---
title: "Secuencia de operaciones para compilar aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [MFC], desarrollar"
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Secuencia de operaciones para compilar aplicaciones MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente explica la secuencia general que puede seguir normalmente mientras desarrolla la aplicación MFC.  
  
### Secuencia para compilar una aplicación con el marco  
  
|Tarea|Hace|Hace el marco|  
|-----------|----------|-------------------|  
|Cree una aplicación esqueleto.|Ejecute [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md).  Especifique las opciones que desee en las páginas opciones.  Las opciones incluyen crear la aplicación al componente COM, el contenedor, o ambos; automatización de suma; y crear la aplicación base de datos\- reconozca.|El asistente para aplicaciones MFC crea los archivos de una aplicación esqueleto, incluidos los archivos de código fuente de la aplicación, el documento, la vista, y las ventanas de marco; un archivo de recursos; un archivo de proyecto; y otros, bien todo a las especificaciones.|  
|Vea lo que proporcionan el marco y el asistente para aplicaciones MFC sin agregar una línea del propio código.|Compile la aplicación esqueleto y ejecútela en Visual C\+\+.|La aplicación esqueleto actual deriva mucho **archivo**estándar, **edición**, **Visualización**, y comandos de menú de **Ay&uda** del marco.  Para las aplicaciones MDI, también obtiene a totalmente \- el menú de Windows funcional, y el marco administra la creación, la organización, y la destrucción de las ventanas MDI secundarias.|  
|Crear la interfaz de usuario de la aplicación.|Utilice Visual C\+\+ [editores de recursos](../mfc/resource-editors.md) para editar visualmente la interfaz de usuario de la aplicación:<br /><br /> -   Crear menús.<br />-   Defina los aceleradores.<br />-   Cree los cuadros de diálogo.<br />-   Crear y editar los mapas de bits, iconos, y los cursores.<br />-   Edite la barra de herramientas creará automáticamente por el asistente para aplicaciones MFC.<br />-   Crear y editar otros recursos.<br /><br /> También puede probar los cuadros de diálogo del editor de cuadros de diálogo.|El archivo de recursos predeterminado creado por el Asistente para aplicaciones proporciona MFC muchos de los recursos que necesita.  Visual C\+\+ permite editar recursos existentes y agregar nuevos recursos con facilidad y visualmente.|  
|Menús a las funciones de controlador.|Use el botón de **Eventos** en [Ventana Propiedades](../Topic/Properties%20Window.md) para conectar menús y los aceleradores a las funciones de controlador en el código.|La ventana Propiedades inserta entradas de mensaje\- mapa y vacía plantillas de función en los archivos de código fuente que especifique y administrar muchas tareas manuales de codificación.|  
|Escriba el código del controlador.|Utilice la vista de clases para saltar directamente al código en el editor de código fuente.  Complete el código para las funciones del controlador.  Para obtener más información sobre cómo utilizar la vista de clases y los asistentes que agregan código a un proyecto, vea [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).|La vista de clases se abre el editor, se desplaza a la plantilla y las posiciones vacías de la función cursor automáticamente.|  
|Botones de la barra de herramientas a los comandos.|Asignar cada botón de la barra de herramientas a un menú o un comando de aceleradores asignando el botón el identificador de comando apropiada|El marco controla el gráfico, habilitar, deshabilitar, comprobar, y otros aspectos visuales de los botones de la barra de herramientas.|  
|Pruebe las funciones controladoras.|Recompile el programa y utilice las herramientas de depuración a punto integradas para probar que los controladores correctamente.|Puede entrar o seguir paso a paso el código para ver cómo se llama a los controladores.  Si ha completado el código del controlador, controladores realizan comandos.  El marco automáticamente deshabilitará los elementos de menú y los botones de la barra de herramientas que no se controlan.|  
|Agregue [cuadros de diálogo](../mfc/dialog-boxes.md).|Diseñar los recursos de la diálogo\- plantilla con el editor de cuadros de diálogo.  A continuación cree una clase de diálogo y el código que controla el cuadro de diálogo.|El marco de trabajo administra el cuadro de diálogo y facilita el recuperar de la información proporcionada por el usuario.|  
|Inicialice, valide, y recupere los datos del cuadro de diálogo.|También puede definir cómo los controles de cuadro de diálogo se deben inicializar y ser validados.  Utilice Visual Studio para agregar a variables miembro a la clase de diálogo y asignarlos a los controles de cuadro de diálogo.  Especifique las reglas de validación para aplicar a cada control como el usuario escriba datos.  Proporcione poseen validaciones personalizadas si desea.|El marco de trabajo administra la inicialización y la validación del cuadro de diálogo.  Si el usuario escribe la información no válida, el marco muestra un cuadro de mensaje y permite al usuario repetir los datos.|  
|Crear clases adicionales.|Utilice la vista de clases para crear el documento adicional, vista, y clases de la cuadro\- ventana más allá de los creados automáticamente el asistente para aplicaciones MFC.  Puede crear clases adicionales del conjunto de registros de la base de datos, clases de diálogo, y así sucesivamente. \(Con la vista de clases, puede crear clases no derivadas de clases MFC\).|La vista de clases agrega estas clases a los archivos de código fuente y le define sus conexiones a cualquier comando lo controla.|  
|Agregar componentes listos para utilizar la aplicación.|Utilice `New Item dialog box` para agregar una variedad de elementos.|Estos elementos son fáciles integrar en la aplicación y ahorrar mucho trabajo.|  
|Implemente la clase del documento.|Implemente la clase o clases específica de la aplicación del documento.  Agregue las variables miembro para contener las estructuras de datos.  Agregue las funciones miembro para proporcionar una interfaz a los datos.|El marco sabe ya interactuar con los archivos de datos del documento.  Puede abrir y cerrar los documentos, leer y escribir los datos del documento, y controla otras interfaces de usuario.  Puede centrarse en cómo se manipula los datos del documento.|  
|Implemente el Abrir, Guardar, y Guardar como comandos.|Escriba el código para la función miembro de `Serialize` del documento.|El marco muestra cuadros de diálogo para **Abierta**, **Guardar**, y los comandos de **Guardar como** en el menú de **archivo** .  Escribe y lee admite un documento con el formato de datos especificado en la función miembro de `Serialize` .|  
|Implemente la clase de vista.|Implemente una o más clases de vista correspondiente a los documentos.  Implemente el miembro de la vista funciona que asignó a la interfaz de usuario con la vista de clases.  Una variedad de [CView](../mfc/reference/cview-class.md)\- clases derivadas están disponibles, incluida [CListView](../mfc/reference/clistview-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).|El marco de trabajo administra la mayor parte de la relación entre un documento y su vista.  Las funciones miembro de vista tienen acceso al documento de la vista para generar la imagen de la pantalla o la página impresa y actualizar las estructuras de datos del documento en respuesta a comandos de edición del usuario.|  
|Impresión predeterminada mejorada.|Si necesita admitir la impresión de varias páginas, el miembro de la vista de reemplazo funciona.|El marco admite **Impresión**, **Configurar página**, y los comandos de **Vista previa de impresión** en el menú de **archivo** .  Debe indicar cómo interrumpir el documento en varias páginas.|  
|Agregue el desplazamiento.|Si necesita admitir el desplazamiento, derive la clase o clases de vista de [CScrollView](../mfc/reference/cscrollview-class.md).|La vista agrega automáticamente las barras de desplazamiento cuando la ventana de vista aumenta demasiado pequeña.|  
|Crear vistas de formulario.|Si desea basar las vistas en recursos de la diálogo\- plantilla, derive la clase o clases de vista de [CFormView](../mfc/reference/cformview-class.md).|Vista utiliza el recurso de la diálogo\- plantilla a los controles de presentación.  El usuario puede pestaña de control al control en la vista.|  
|Crear formularios de base de datos.|Si desea que una aplicación de acceso a datos formulario\- basada, derive la clase de vista de [CRecordView](../mfc/reference/crecordview-class.md) \(para ODBC que programa\).|La vista funciona como una vista de formulario, pero sus controles están conectados a los campos de un objeto de [CRecordset](../mfc/reference/crecordset-class.md) que representa una tabla de base de datos.  MFC mover datos entre los controles y el conjunto de registros para usted.|  
|Cree un editor de texto simple.|Si desea que la vista para ser el editor de texto simple, derive la clase o clases de vista de [CEditView](../mfc/reference/ceditview-class.md) o de [CRichEditView](../mfc/reference/cricheditview-class.md).|La vista proporciona funciones de edición, la compatibilidad del portapapeles, y la entrada del archivo.  `CRichEditView` proporciona texto con estilo.|  
|Agregue las ventanas divisoras.|Si desea admitir la ventana que divide, agregue un objeto de [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) a la ventana de marco SDI o la ventana secundaria y enlace de MDI él en la función miembro de [OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md) de la ventana.|Los controles de divisor\- cuadro de fuentes de marco junto a las barras de desplazamiento y administran dividir la vista en varios paneles.  Si el usuario divide una ventana, el marco de trabajo crea y adjunta objetos de vista adicionales al documento.|  
|Compilar, probar, y depure la aplicación.|Utilice las utilidades de Visual C\+\+ para compilar, probar, y depurar la aplicación.|Visual C\+\+ permite ajustar compilación, el vínculo, y otras opciones.  También permite examinar la estructura del código fuente y clases.|  
  
## Vea también  
 [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [Compilar en el marco](../mfc/building-on-the-framework.md)