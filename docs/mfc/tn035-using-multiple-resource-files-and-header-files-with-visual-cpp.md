---
title: "TN035: Usar varios archivos de recursos y archivos de encabezado con Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resources"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de recursos, varios"
  - "TN035"
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN035: Usar varios archivos de recursos y archivos de encabezado con Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo el editor de recursos de Visual C\+\+ permite compartir varios archivos de recursos y archivos de encabezado en un solo proyecto o entre varios proyectos y cómo se puede aprovechar esa característica.  Esta nota responde a estas preguntas:  
  
-   ¿Cuándo se podría desear dividir un proyecto en varios archivos de recursos o archivos de encabezado y cómo se hace?  
  
-   ¿Cómo se comparte un archivo .H de encabezado común entre dos archivos .RC?  
  
-   ¿Cómo se dividen recursos de proyecto en varios archivos .RC?  
  
-   ¿Cómo administra el usuario \(y las herramientas\) las dependencias de compilación entre archivos .RC, .CPP y .H?  
  
 Debe tener en cuenta que si agrega un archivo de recursos adicional al proyecto, ClassWizard no reconocerá los recursos en el archivo agregado.  
  
 Esta nota está estructurada para responder a las preguntas anteriores de la manera siguiente:  
  
-   **Overview of How Visual C\+\+ Manages Resource Files and Header Files** proporciona información general sobre cómo el comando de inclusión de conjuntos de recursos de Visual C\+\+ permite utilizar archivos de recursos y archivos de encabezado en el mismo proyecto.  
  
-   **Analysis of AppWizard\-created .RC and .H Files** examina los diversos archivos de recursos y encabezado usados por una aplicación creada mediante AppWizard.  Estos archivos son un buen modelo para los archivos de recursos y de encabezado adicionales que puede agregar al proyecto.  
  
-   **Including Additional Header Files** describe dónde debería incluir los archivos de encabezado y proporciona detalles de cómo hacerlo.  
  
-   **Sharing a Header File Between Two .RC Files** muestra cómo se puede compartir un archivo de encabezado entre varios archivos .RC de diferentes proyectos o, quizá, del mismo proyecto.  
  
-   **Using Multiple Resource Files in the Same Project** describe dónde puede dividir el proyecto en varios archivos .RC y proporciona detalles de cómo hacerlo.  
  
-   **Enforcement of Non\-Editable Visual C\+\+ Files** describe cómo puede asegurarse de que Visual C\+\+ no modifique ni cambie involuntariamente el formato de un recurso personalizado.  
  
-   **Managing Symbols Shared by Multiple Visual C\+\+\-Edited .RC Files** describe cómo compartir los mismos símbolos entre varios archivos .RC y cómo evitar asignar valores numéricos de identificador duplicados.  
  
-   **Managing Dependencies Between .RC, .CPP, and .H Files** describe cómo Visual C\+\+ evita la recompilación innecesaria de archivos .CPP dependientes de los archivos de símbolos de recursos.  
  
-   **How Visual C\+\+ Manages Set Includes Information** proporciona detalles técnicos sobre cómo realiza Visual C\+\+ el seguimiento de los varios archivos .RC \(anidados\) y varios archivos de encabezado especificados con \#include en un archivo .RC.  
  
 **Información general sobre cómo administra Visual C\+\+ archivos de recursos y archivos de encabezado**  
  
 Visual C\+\+ administra un único archivo de recursos de .RC y un archivo de encabezado .H correspondiente como un par de archivos estrechamente acoplado.  Al modificar y guardar los recursos en un archivo .RC, puede editar y guardar símbolos indirectamente en el correspondiente archivo .H.  Aunque puede abrir y editar varios archivos .RC al mismo tiempo \(mediante la interfaz de usuario MDI de Visual C\+\+\) para cualquier archivo .RC dado, de manera indirecta se edita exactamente un archivo de encabezado correspondiente.  
  
 **Archivo de encabezado de símbolos**  
  
 De forma predeterminada, Visual C\+\+ nombra siempre el archivo de encabezado correspondiente RESOURCE.H, sin importar el nombre del archivo de recursos \(por ejemplo, MYAPP.RC\).  Mediante el comando **Archivos de inclusión de recursos** del menú **Ver** de Visual C\+\+, puede cambiar el nombre de este archivo de encabezado actualizando el archivo de encabezado de símbolos en el cuadro de diálogo **Archivos de inclusión establecidos**.  
  
 **Directivas de símbolos de solo lectura**  
  
 Aunque Visual C\+\+ solo edita un archivo de encabezado para cualquier archivo dado de .RC, Visual C\+\+ admite referencias a símbolos definidos en archivos de encabezado de solo lectura adicionales.  Mediante el comando **Archivos de inclusión de recursos** del menú **Ver** de Visual C\+\+, puede especificar cualquier número de archivos de encabezado de solo lectura adicionales como directivas símbolos de solo lectura.  La restricción "solo lectura" significa que al agregar un nuevo recurso al archivo .RC, puede utilizar un símbolo definido en el archivo de encabezado de solo lectura; pero, si elimina el recurso, el símbolo continuará estando definido en el archivo de encabezado de solo lectura.  No se puede cambiar el valor numérico asignado a un símbolo de solo lectura.  
  
 **Directivas de tiempo de compilación**  
  
 Visual C\+\+ admite también el anidamiento de archivos de recursos, donde un archivo .RC está especificado con \#include dentro de otro.  Al editar un archivo .RC determinado mediante Visual C\+\+, los recursos de los archivos especificados con \#include no son visibles.  Pero, cuando se compila el archivo .RC, los archivos especificados con \#include también se compilan.  Mediante el comando **Archivos de inclusión de recursos** del menú **Ver** en Visual C\+\+, puede especificar cualquier número de archivos .RC especificados con \#include como directivas de tiempo de compilación.  
  
 Observe qué ocurre si se lee en Visual C\+\+ un archivo .RC que especifique con \#include otro archivo .RC que *no* se especifique como directiva de tiempo de compilación.  Esta situación podría surgir al llevar a Visual C\+\+ un archivo .RC que se haya mantenido previamente de manera manual con un editor de texto.  Cuando Visual C\+\+ lee el archivo .RC especificado con \#include, combina los recursos especificados con \#include en el archivo .RC principal.  Cuando se guarde el archivo .RC principal, la instrucción \#include se reemplazará por los recursos especificados con \#include.  Si no desea que se produzca esta combinación, debe quitar la instrucción \#include del archivo .RC principal *antes* de leerlo en Visual C\+\+; a continuación, utilizando Visual C\+\+, vuelva a agregar la misma instrucción \#include como una directiva de tiempo de compilación.  
  
 Visual C\+\+ guarda en un archivo .RC las tres clases anteriores de información establecida de inclusión \(archivo de encabezado de símbolos, directivas de símbolos de solo lectura y directivas en tiempo de compilación\) en directivas \#include *y* en recursos TEXTINCLUDE.  Los recursos TEXTINCLUDE, un detalle de implementación del normalmente no hay que preocuparse, se explican en [Cómo administra Visual C\+\+ la información de inclusión establecida](#_mfcnotes_tn035_set_includes).  
  
 **Análisis de archivos .RC y .H creados mediante AppWizard**  
  
 El examen del código de aplicación generado por AppWizard proporciona una idea clara de cómo Visual C\+\+ administra varios archivos de recursos y archivos de encabezado.  Los extractos de código que se examinan a continuación proceden de una aplicación MYAPP generada mediante AppWizard con las opciones predeterminadas.  
  
 Una aplicación creada mediante AppWizard utiliza varios archivos de recursos y varios archivos de encabezado, como se resume en el diagrama siguiente:  
  
```  
RESOURCE.H     AFXRES.H                      
       \       /                                
        \     /                                  
       MYAPP.RC                                 
           |                                  
           |                                
     RES\MYAPP.RC2    
     AFXRES.RC                     
     AFXPRINT.RC                   
```  
  
 Puede ver estas relaciones de varios archivos mediante el comando de inclusión de archivos de Visual C\+\+.  
  
 MYAPP.RC  
 El archivo de recursos de la aplicación que se edita mediante Visual C\+\+.  
  
 RESOURCE.H es el archivo de encabezado específico de la aplicación.  AppWizard siempre lo llama RESOURCE.H, de manera coherente con la denominación predeterminada de Visual C\+\+ para el archivo de encabezado.  La instrucción \#include para este archivo de encabezado es la primera instrucción del archivo de recursos \(MYAPP.RC\):  
  
```  
//Microsoft Visual C++ generated resource script  
//  
#include "resource.h"  
```  
  
 RES\\MYAPP.RC2  
 Contiene recursos que no se editarán en Visual C\+\+ pero se incluirán en el archivo compilado final .EXE.  AppWizard no crea tales recursos de forma predeterminada, ya que Visual C\+\+ puede editar todos los recursos estándar, incluido el recurso de versión \(una nueva característica de esta versión\).  AppWizard genera un archivo vacío en caso de que desee agregar sus propios recursos con formato personalizado a este archivo.  
  
 Si utiliza recursos con formato personalizado, puede agregarlos a RES\\MYAPP.RC2 y modificarlos con el editor de texto de Visual C\+\+.  
  
 AFXRES.RC y AFXPRINT.RC contienen recursos estándar necesarios para ciertas características de .NET Framework.  Como RES\\MYAPP.RC2, estos dos archivos de recursos proporcionados por .NET Framework se especifican con \#include al final de MYAPP.RC y se especifican en las directivas de tiempo de compilación del cuadro de diálogo Archivos de inclusión establecidos.  Por tanto, no verá ni editará directamente estos recursos de .NET Framework mientras edite MYAPP.RC en Visual C\+\+, pero se compilarán en el archivo binario de .RES de la aplicación y en el archivo final .EXE.  Para obtener más información sobre los recursos estándar de .NET framework, incluidos los procedimientos para modificarlos, vea la [Nota técnica 23](../mfc/tn023-standard-mfc-resources.md).  
  
 AFXRES.H define símbolos estándar, tales como `ID_FILE_NEW`, usados por .NET Framework y, específicamente, en AFXRES.RC.  AFXRES.H también especifica mediante \#include WINRES.H, que contiene un subconjunto de WINDOWS.H necesario para los archivos .RC generados por Visual C\+\+, así como AFXRES.RC.  Los símbolos definidos en AFXRES.H están disponibles cuando se edita el archivo de recursos de la aplicación \(MYAPP.RC\).  Por ejemplo, `ID_FILE_NEW` se utiliza para el elemento de menú de Archivo Nuevo en recursos de menús de MYAPP.RC.  No se puede cambiar ni eliminar estos símbolos definidos por .NET framework.  
  
 **Incluir archivos de encabezado adicionales**  
  
 La aplicación creada mediante AppWizard incluye solo dos archivos de encabezado: RESOURCE.H y AFXRES.H.  Solo RESOURCE.H es específico de la aplicación.  Puede ser necesario incluir archivos de encabezado de solo lectura adicionales en los casos siguientes:  
  
 El archivo de encabezado lo proporciona un origen externo o desea compartir el archivo de encabezado entre varios proyectos o partes diferentes del mismo proyecto.  
  
 El archivo de encabezado tiene formato y comentarios que no desea que Visual C\+\+ modifique o filtre cuando guarde el archivo.  Por ejemplo, quizá desee conservar las instrucciones \#define que utilicen aritmética simbólica, tales como:  
  
```  
#define RED 0  
#define BLUE 1  
#define GREEN 2  
#define ID_COLOR_BUTTON 1001  
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)  
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)  
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)  
```  
  
 Puede incluir archivos de encabezado de solo lectura adicionales mediante el comando **Archivos de inclusión de recursos** para especificar la instrucción \#include como segunda directiva de símbolos de solo lectura, como en:  
  
```  
#include "afxres.h"  
#include "second.h"  
```  
  
 El nuevo diagrama de relación entre archivos tiene ahora el siguiente aspecto:  
  
```  
               AFXRES.H         
RESOURCE.H     SECOND.H                      
      \       /                                
       \     /                                  
      MYAPP.RC     
          |                                  
          |                                
    RES\MYAPP.RC2    
    AFXRES.RC                     
    AFXPRINT.RC                   
```  
  
 **Compartir un archivos de encabezado entre dos archivos .RC**  
  
 Quizá desee compartir un archivo de encabezado entre dos archivos .RC que estén en proyectos diferentes o, posiblemente, en el mismo proyecto.  Para ello, solo tiene que aplicar la técnica de directivas de solo lectura descrita anteriormente a ambos archivos .RC.  Si los dos archivos .RC son para aplicaciones diferentes \(proyectos diferentes\), el resultado se muestra en el diagrama siguiente:  
  
```  
     RESOURCE.H   AFXRES.H   RESOURCE.H    
    (for MYAPP1)  SECOND.H   (for MYAPP2)               
          \       /     \       /             
           \     /       \     /               
          MYAPP1.RC      MYAPP2.RC                   
           /    \        /     \                     
          /      \      /       \              
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2                
                AFXPRINT.RC                   
```  
  
 El caso donde el segundo archivo de encabezado es compartido por dos archivos .RC en la misma aplicación \(proyecto\) se describe a continuación.  
  
 **Usar varios archivos de recursos en el mismo proyecto**  
  
 Visual C\+\+ y el compilador de recursos admiten varios archivos .RC en el mismo proyecto mediante instrucciones \#include de un archivo .RC dentro de otro.  Se permite el anidamiento de varios niveles.  Hay varias razones para dividir los recursos del proyecto en varios archivos .RC:  
  
-   Es más fácil administrar un gran número de recursos entre varios miembros del equipo del proyecto si se dividen los recursos en varios archivos .RC.  Si utiliza un paquete de administración de control de código fuente para desproteger los archivos y proteger los cambios, dividir los recursos en varios archivos .RC producirá un control más preciso sobre la administración de cambios en los recursos.  
  
-   Si desea utilizar directivas de preprocesador, tales como \#ifdef, \#endif y \#define, para partes de los recursos, debe aislarlos en recursos de solo lectura que se compilarán mediante el compilador de recursos.  
  
-   Los archivos .RC componentes se cargarán y guardarán más rápidamente en Visual C\+\+ que un archivo .RC compuesto.  
  
-   Si desea mantener un recurso con un editor de texto en un formato legible, debe mantenerlo en un archivo .RC independiente del que edite Visual C\+\+.  
  
-   Si necesita conservar un recurso definido por el usuario en un archivo de formato binario o de texto que sea interpretable por otro editor de datos especializado, debe mantenerlo en un archivo .RC independiente para que Visual C\+\+ no cambie el formato a datos hexadecimales.  Los recursos de archivo .WAV \(sonido\) del ejemplo de conceptos avanzados de [SPEAKN](../top/visual-cpp-samples.md) son un buen ejemplo.  
  
 Puede usar \#include con SECOND.RC en las directivas de tiempo de compilación en el cuadro de diálogo Archivos de inclusión establecidos:  
  
```  
#include "res\myapp.rc2"  // non-Visual C++ edited resources  
#include "second.rc"  // THE SECOND .RC FILE  
  
#include "afxres.rc"  // Standard components  
#include "afxprint.rc"  // printing/print preview resources  
```  
  
 El resultado se describe en el diagrama siguiente:  
  
```  
RESOURCE.H     AFXRES.H                      
       \       /                                
        \     /                                  
       MYAPP.RC  
           |                                  
           |                                
     RES\MYAPP.RC2  
     SECOND.RC    
     AFXRES.RC                     
     AFXPRINT.RC                   
```  
  
 Si usa directivas de tiempo de compilación, puede organizar los recursos editables y no editables de Visual C\+\+ en varios archivos .RC, donde el archivo MYAPP.RC "principal" no hace nada pero especifica mediante \#include los otros archivos .RC.  Si utiliza un archivo .MAK de proyecto de Visual C\+\+, debe incluir el archivo .RC "principal" en el proyecto para que todos los recursos especificados con \#include se compilen con la aplicación.  
  
 **Cumplimiento de archivos no editables de Visual C\+\+**  
  
 El archivo RES\\MYAPP.R C2 creado mediante AppWizard es un ejemplo de archivo que contiene recursos que *no* se desea que se lean accidentalmente en Visual C\+\+ y, a continuación, se vuelvan a escribir con pérdida de información de formato.  Para protegerse de esto, coloque las siguientes líneas al principio del archivo RES\\MYAPP.RC2:  
  
```  
#ifdef APSTUDIO_INVOKED  
    #error this file is not editable by Visual C++  
#endif //APSTUDIO_INVOKED  
```  
  
 Cuando Visual C\+\+ compila el archivo .RC, define **APSTUDIO\_INVOKED**, así como **RC\_INVOKED**.  Si se daña la estructura de archivos creada mediante AppWizard creada y Visual C\+\+ lee la línea \#error anterior, notifica un error irrecuperable y anula la lectura del archivo .RC.  
  
 **Administrar símbolos compartidos por varios archivos .RC editados por Visual C\+\+**  
  
 Cuando se dividen los recursos en varios archivos .RC que se desea editar por separado en Visual C\+\+ surgen dos problemas:  
  
-   Quizás desee compartir los mismos símbolos entre varios archivos .RC.  
  
-   Debe ayudar a Visual C\+\+ a evitar que asigne los mismos valores numéricos de id. a distintos recursos \(símbolos\).  
  
 En el diagrama siguiente se muestra una organización de archivos .RC y.H que se ocupa del primer problema:  
  
```  
              MYAPP.RC  
             /         \  
            /           \  
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H  
     \    /    /      \   \    \  
      \  /    /        \   \    \  
   MYSTRS.RC           MYMENUS.RC  
```  
  
 En este ejemplo, los recursos de cadena se mantienen en un archivo de recursos, MYSTRS.RC y los menús se mantienen en otro, MYMENUS.RC.  Es posible que algunos símbolos, por ejemplo para comandos, deban compartirse entre los dos archivos.  Por ejemplo, ID\_TOOLS\_SPELL puede ser el identificador de comando de menú para el elemento Ortografía de un menú Herramientas; y también puede ser el identificador de cadena del símbolo del sistema que .NET framework muestra en la barra de estado de la ventana principal de la aplicación.  
  
 El símbolo ID\_TOOLS\_SPELL se mantiene en el archivo de encabezado compartido, MYSHARED.H.  Este archivo de encabezado compartido se mantiene manualmente con un editor de texto; Visual C\+\+ no lo edita directamente.  En los dos archivos de recursos MYSTRS.RC y MYMENUS.RC, especifique \#include MYSHARED.H en las directivas de solo lectura para MYAPP.RC mediante el comando **Archivos de inclusión de recursos**, como se describió anteriormente.  
  
 Es más conveniente prever el símbolo que se compartirá antes de intentar usarlo para identificar cualquier recurso.  Agregue el símbolo al archivo de encabezado compartido y, si aún no ha especificado con \#include el archivo de encabezado compartido en las directivas de solo lectura para el archivo .RC, hágalo antes de utilizar el símbolo.  Si no ha previsto compartir el símbolo de esta manera, tendrá que mover manualmente \(mediante un editor de texto\) la instrucción \#define para el símbolo desde, por ejemplo, MYMENUS.H hasta MYSHARED.H antes de utilizarla en MYSTRS.RC.  
  
 Cuando administre símbolos en varios archivos .RC, también debe ayudar a Visual C\+\+ a evitar asignar los mismos valores numéricos de id. a recursos \(símbolos\) distintos.  Para cualquier archivo .RC dado, Visual C\+\+ asigna id. de manera incremental en cada uno de estos cuatro dominios de id.  Entre las sesiones de edición, Visual C\+\+ realiza un seguimiento del último id. asignado en cada uno de los dominios del archivo de encabezado de símbolos para el archivo .RC.  Estos son los valores de APS\_NEXT para un archivo .RC vacío \(nuevo\):  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  101  
#define _APS_NEXT_COMMAND_VALUE   40001  
#define _APS_NEXT_CONTROL_VALUE   1000  
#define _APS_NEXT_SYMED_VALUE     101  
```  
  
 **\_APS\_NEXT\_RESOURCE\_VALUE** es el siguiente valor de símbolo que se utilizará para un recurso de cuadro de diálogo, un recurso de menú y así sucesivamente.  El intervalo válido para los valores de símbolos de recursos es de 1 a 0x6FFF.  
  
 **\_APS\_NEXT\_COMMAND\_VALUE** es el siguiente valor de símbolo que se utilizará para una identificación de comando.  El intervalo válido para los valores de símbolos de comando es 0x8000 a 0xDFFF.  
  
 **\_APS\_NEXT\_CONTROL\_VALUE** es el siguiente valor de símbolo que se utilizará para un control de cuadro de diálogo.  El intervalo válido para los valores de símbolo de control del diálogo es de 8 a 0xDFFF.  
  
 **\_APS\_NEXT\_SYMED\_VALUE** es el siguiente valor de símbolo que se emitirá al asignar manualmente un valor de símbolo mediante el comando Nuevo del explorador de símbolos.  
  
 Visual C\+\+ comienza con valores ligeramente superiores al valor legal inferior al crear un nuevo archivo .RC.  AppWizard también inicializará estos valores a algo más adecuado para aplicaciones MFC.  Para obtener más información acerca de los intervalos de valores de id., vea la [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md).  
  
 Ahora, cada vez que se crea un nuevo archivo de recursos, incluso en el mismo proyecto, Visual C\+\+ define los mismos valores de **\_APS\_NEXT\_**.  Esto significa que si agrega, por ejemplo, varios diálogos en dos archivos .RC diferentes, es muy probable que se asigne el mismo valor \#define a diferentes diálogos.  Por ejemplo, IDD\_MY\_DLG1 en el primer archivo .RC podría estar asignado al mismo número, 101, que IDD\_MY\_DLG2 en un segundo archivo .RC.  
  
 Para evitar esto, debe reservar un intervalo numérico independiente para cada uno de los cuatro dominios de id. en los respectivos archivos .RC.  Haga esto manualmente actualizando los valores de **\_APS\_NEXT** en cada uno de los archivos .RC `before` de empezar a añadir recursos.  Por ejemplo, si el primer archivo .RC utiliza los valores predeterminados de **\_APS\_NEXT**, puede que a continuación desee asignar los siguientes valores de **\_APS\_NEXT** al segundo archivo .RC:  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  2000  
#define _APS_NEXT_COMMAND_VALUE   42000  
#define _APS_NEXT_CONTROL_VALUE   2000  
#define _APS_NEXT_SYMED_VALUE     2000  
```  
  
 Por supuesto, continúa siendo posible que Visual C\+\+ asigne tantos id. en el primer archivo .RC que los valores numéricos empiecen a superponerse a los reservados para el segundo archivo .RC.  Debe reservar intervalos suficientemente grandes para que no ocurra esto.  
  
 **Administrar dependencias entre archivos .RC, .CPP y .H**  
  
 Cuando Visual C\+\+ guarda un archivo .RC, también guarda los cambios de símbolos en archivo RESOURCE.H correspondiente.  Cualquiera de los archivos .CPP que hacen referencia a recursos del archivo .RC deben incluir con \#include el archivo RESOURCE.H, normalmente en el archivo de encabezado del proyecto principal.  Esto provoca un efecto secundario no deseado debido a la administración de proyectos interna del entorno de desarrollo, que examina los archivos de código fuente para detectar dependencias de encabezado.  Cada vez que se agrega un nuevo símbolo en Visual C\+\+, todo el archivo .CPP que incluye con \#include RESOURCE.H debe volver a compilarse.  
  
 Visual C\+\+ evita la dependencia de RESOURCE.H incluyendo el siguiente comentario como primera línea del archivo RESOURCE.H:  
  
```  
//{{NO_DEPENDENCIES}}  
```  
  
 El entorno de desarrollo interpreta este comentario omitiendo los cambios en RESOURCE.H para que no sea necesario recompilar los archivos .CPP dependientes.  
  
 Visual C\+\+ agrega siempre la línea de comentario \/\/{{NO\_DEPENDENCIES}} a un archivo .RC cuando guarda el archivo.  En algunos casos, evitar la dependencia de compilación de RESOURCE.H puede provocar errores en tiempo de ejecución que no se detectan en tiempo de vinculación.  Por ejemplo, si utiliza el explorador de símbolos para cambiar el valor numérico asignado a un símbolo para un recurso, el recurso no se encontrará correctamente y no se cargará en tiempo de ejecución de la aplicación si no se vuelve a compilar el archivo .CPP que hace referencia al recurso.  En estos casos, se debe volver a compilar explícitamente los archivos .CPP que se sepan afectados por los cambios de símbolos en RESOURCE.H o seleccione **Volver a generar todo**.  Si necesita cambiar con frecuencia valores de símbolos para un determinado grupo de recursos, es probable que le resulte más cómodo y seguro dividir estos símbolos en un archivo de encabezado de solo lectura independiente, como se describe en la sección anterior [Archivos de encabezado de inclusión adicionales](#_mfcnotes_tn035_including).  
  
 **Cómo administra Visual C\+\+ la información de inclusión establecida**  
  
 Tal y como se describió anteriormente, el comando de inclusión del menú Archivo permite especificar tres tipos de información:  
  
-   Archivo de encabezado de símbolos  
  
-   Directivas de símbolos de solo lectura  
  
-   Directivas de tiempo de compilación  
  
 A continuación se describe cómo mantiene Visual C\+\+ esta información en un archivo .RC.  No necesita esta información para utilizar Visual C\+\+, pero puede mejorar su comprensión para que pueda usar con más confianza la característica de inclusión.  
  
 Cada uno de los tres tipos anteriores de información de inclusión se almacena en el archivo .RC de dos formas: \(1\) como \#include u otras directivas interpretables mediante el compilador de recursos y \(2\), como recursos especiales TEXTINCLUDE interpretables solo por Visual C\+\+.  
  
 El propósito del recurso TEXTINCLUDE es almacenar con seguridad información de inclusión en una forma que sea fácilmente presentable en el cuadro de diálogo **Archivos de inclusión establecidos** de Visual C\+\+.  TEXTINCLUDE es un *tipo de recurso* definido por Visual C\+\+.  Visual C\+\+ reconoce tres recursos TEXTINCLUDE específicos que tienen los números de identificación de recurso 1, 2 y 3:  
  
|Id. de recurso TEXTINCLUDE|Tipo de información de inclusión|  
|--------------------------------|--------------------------------------|  
|1|Archivo de encabezado de símbolos|  
|2|Directivas de símbolos de solo lectura|  
|3|Directivas de tiempo de compilación|  
  
 Los archivos MYAPP.RC y RESOURCE.H predeterminados creados por AppWizard ilustran los tres tipos de información de inclusión, como se describe a continuación.  La sintaxis de RC requiere los tokens adicionales \\0 y "" entre los bloques BEGIN y END para especificar cadenas terminadas en cero y el carácter de comilla doble, respectivamente.  
  
## Archivo de encabezado de símbolos  
 El formato de la información de archivo de encabezado de símbolos interpretada mediante el compilador de recursos es simplemente una instrucción \#include:  
  
```  
#include "resource.h"  
```  
  
 El recurso TEXTINCLUDE correspondiente es:  
  
```  
1 TEXTINCLUDE DISCARDABLE  
BEGIN  
   "resource.h\0"  
END  
```  
  
## Directivas de símbolos de solo lectura  
 Las directivas de símbolos de solo lectura se incluyen al principio de MYAPP.RC con el siguiente formato interpretable por el compilador de recursos:  
  
```  
#include "afxres.h"  
```  
  
 El recurso TEXTINCLUDE correspondiente es:  
  
```  
2 TEXTINCLUDE DISCARDABLE  
BEGIN  
   "#include ""afxres.h""\r\n"  
   "\0"  
END  
```  
  
## Directivas de tiempo de compilación  
 Las directivas de tiempo de compilación se incluyen al final de MYAPP.RC con el siguiente formato interpretable por el compilador de recursos:  
  
```  
#ifndef APSTUDIO_INVOKED  
///////////////////////  
//  
// From TEXTINCLUDE 3  
//  
#include "res\myapp.rc2"  // non-Visual C++ edited resources  
  
#include "afxres.rc"  // Standard components  
#include "afxprint.rc"  // printing/print preview resources  
#endif  // not APSTUDIO_INVOKED  
```  
  
 La directiva \#ifndef APSTUDIO\_INVOKED indica a Visual C\+\+ que omita las directivas de tiempo de compilación.  
  
 El recurso TEXTINCLUDE correspondiente es:  
  
```  
3 TEXTINCLUDE DISCARDABLE  
BEGIN  
"#include ""res\myapp.rc2""  // non-Visual C++ edited resources\r\n"  
"\r\n"  
"#include ""afxres.rc""  // Standard components\r\n"  
"#include ""afxprint.rc""  // printing/print preview resources\r\n"  
"\0"  
END  
```  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)