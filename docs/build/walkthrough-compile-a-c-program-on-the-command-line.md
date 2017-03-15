---
title: "Tutorial: Compilar un programa escrito en C en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "compilar un programa escrito en C [C++]"
  - "aplicaciones de línea de comandos [C++], programas escritos en C"
  - "compilar programas [C++]"
  - "Visual C, compilar"
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
caps.latest.revision: 46
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# Tutorial: Compilar un programa escrito en C en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] incluye un compilador de C que puede usar para crear desde programas básicos de la consola hasta aplicaciones de escritorio de Windows.  
  
 Este tutorial muestra cómo crear un programa de C básico con un editor de texto y, a continuación, compilarlo en la línea de comandos.  
  
 Puede usar sus propios programas de C en lugar de escribir los que se muestran en este tutorial a modo de ejemplo.  También puede usar cualquiera de los programas de ejemplo de código de C incluidos en los temas de la Ayuda.  
  
 De forma predeterminada, el compilador de Visual C\+\+ trata todos los archivos que finalizan en .c como código fuente de C, y todos los archivos que finalizan en .cpp como código fuente de C\+\+.  Para hacer que el compilador trate todos los archivos como código fuente de C sin tener en cuenta la extensión del nombre de archivo, use la opción [\/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) del compilador.  
  
## Requisitos previos  
 Debe entender los principios del lenguaje C.  
  
### Para crear un archivo de origen de C y compilarlo en la línea de comandos  
  
1.  Abra un símbolo del sistema del desarrollador.  En Windows 8, en la pantalla **Inicio**, abra la carpeta **Visual Studio Tools** y, luego, elija el acceso directo **Símbolo del sistema para desarrolladores**.  En las versiones anteriores de Windows, elija el botón **Inicio**, expanda **Todos los programas**, **Microsoft Visual Studio** y **Visual Studio Tools** y, luego, elija **Símbolo del sistema para desarrolladores**.  
  
     En función de la versión de Windows del equipo y de la configuración de seguridad del sistema, es posible que deba abrir el menú contextual del **Símbolo del sistema para desarrolladores** y, a continuación, elegir **Ejecutar como administrador** para compilar y ejecutar correctamente la aplicación que se crea siguiendo estos pasos.  
  
    > [!NOTE]
    >  El **Símbolo del sistema para desarrolladores** establece automáticamente la ruta de acceso correcta del compilador de C y de cualquier biblioteca necesaria.  Utilícelo en lugar de la ventana Símbolo del sistema normal.  Para obtener más información, consulte [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
2.  En el símbolo del sistema, cree un directorio para el archivo de código fuente y conviértalo en el directorio de trabajo actual.  Por ejemplo, escriba **md c:\\simple** y presione ENTRAR para crear un directorio llamado simple y, luego, escriba **cd c:\\simple** y presione ENTRAR para cambiar a ese directorio.  
  
3.  En el símbolo del sistema, escriba **notepad** y presione Intro.  
  
4.  En el Bloc de notas, escriba las líneas siguientes.  
  
     [!code-cpp[NVC_Walkthrough_Compile_C#100](../build/codesnippet/CPP/walkthrough-compile-a-c-program-on-the-command-line_1.c)]  
  
5.  En la barra de menús, elija **Archivo**, **Guardar** para abrir el cuadro de diálogo **Guardar como**.  Navegue al directorio que creó.  En el cuadro **Nombre de archivo**, escriba un nombre para el archivo de código fuente \(por ejemplo, simple.c\) y, a continuación, en la lista desplegable **Guardar como tipo**, seleccione **Todos los archivos \(\*.\*\)**.  Elija el botón **Guardar** para crear el archivo de código fuente C en el directorio de trabajo.  
  
6.  En el símbolo del sistema, escriba **dir** y presione Intro.  Debería ver el archivo de origen que creó:  
  
  **C:\\simple\>dir**  
 **El volumen de la unidad C no tiene etiqueta.  El número de serie del volumen es CC62\-6545**  
 **Directorio de C:\\simple**  
**10\/02\/2012  03:46 PM    \<DIR\>          .  10\/02\/2012  03:46 PM    \<DIR\>          ..  10\/02\/2012  03:36 PM               102 simple.c**  
 **1 File\(s\)      102 bytes**  
 **2 Dir\(s\)  514.900.566.016 bytes free**      Los detalles variarán en su equipo.  Si no ve el archivo de código fuente, asegúrese de que cambió al directorio creado y de que guarda el archivo de origen en él con la extensión de nombre de archivo .c.  
  
7.  En el símbolo del sistema, especifique el comando de **cl** junto con el nombre del archivo de código fuente \(por ejemplo, **cl simple.c**\) y presione Intro para compilar el programa.  El compilador cl.exe genera un archivo .obj que contiene el código compilado y, después, ejecuta el enlazador para compilar un programa ejecutable que tenga el nombre del archivo de origen y la extensión de nombre de archivo .exe: por ejemplo, simple.exe.  
  
     Puede ver el nombre del programa ejecutable en las líneas de información de salida que muestra el compilador.  
  
     **Resultado**  
  
  **Compilador de optimización de C\/C\+\+ de Microsoft \(R\) versión 17.00.50727.1 para x86**  
**Copyright \(C\) Microsoft Corporation.  Todos los derechos reservados.  simple.c**  
**Microsoft \(R\) Incremental Linker Version 11.00.50727.1**  
**Copyright \(C\) Microsoft Corporation.  Todos los derechos reservados.  \/out:simple.exe**  
**simple.obj**      El número de versión de las herramientas depende de la versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y de las actualizaciones instaladas.  
  
    > [!NOTE]
    >  Si aparece un error, como “'cl' no se reconoce como un comando interno o externo, programa o archivo por lotes ejecutable” o los errores C1034 o LNK1104, debe establecer el entorno para el compilador y las herramientas.  Para más información, revise el paso 1.  
    >   
    >  Si recibe una advertencia o error del compilador, revise el código fuente para ver los errores, guárdelo y vuelva a ejecutar el compilador.  Para más información sobre errores específicos, use el cuadro de búsqueda de esta página.  
  
8.  Para ejecutar el programa, escriba su nombre sin la extensión de nombre de archivo \(por ejemplo, **simple**\) y presione Intro.  
  
     El programa muestra este texto y, a continuación, se cierra:  
  
     `This is a native C program.`  
  
## Vea también  
 [Tutorial: Crear un programa de consola Win32 \(C\+\+\)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [Referencia de lenguaje C](../c-language/c-language-reference.md)   
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)   
 [Compatibilidad](../c-runtime-library/compatibility.md)