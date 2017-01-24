---
title: "Novedades de Office Developer Tools para Visual Studio 2013 – Actualizaci&#243;n de marzo de 2014 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e701c650-2a2b-4b18-9f7b-04d4fc59a05d
caps.latest.revision: 2
caps.handback.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Novedades de Office Developer Tools para Visual Studio 2013 – Actualizaci&#243;n de marzo de 2014
**Office Developer Tools para Visual Studio 2013 – Actualización de marzo de 2014** incluye muchas características nuevas que mejoran las herramientas incluidas en Visual Studio 2013 para aplicaciones empresariales de nube y aplicaciones para desarrollo de Office y SharePoint.  También permite compilar nuevos tipos de aplicaciones de Office que se permiten en Office 2013 SP1 y Office 365.  
  
-   [Novedades en las aplicaciones empresariales de nube](#cba)  
  
-   [Novedades en el desarrollo de aplicaciones para Office](#office)  
  
-   [Novedades en el desarrollo de aplicaciones para SharePoint](#sharepoint)  
  
##  <a name="cba"></a> Novedades en las aplicaciones empresariales de nube  
 En Visual Studio 2013 se introdujo la plantilla de proyecto de aplicación empresarial de nube, que permite compilar rápidamente aplicaciones empresariales modernas que se integran con la plataforma de Office 365 y mejoran la experiencia con la misma.  En esta versión, se han agregado nuevas características que aportan una mayor compatibilidad para la conexión a datos empresariales y la integración de bibliotecas de documentos, así como mayor compatibilidad para el desarrollo rápido de aplicaciones.  
  
### Asociar a datos empresariales  
 **Nuevo origen de datos SAP**  
  
 Los datos empresariales desempeñan un rol clave en muchas aplicaciones empresariales.  Existen muchos tipos diferentes de orígenes de datos empresariales en el mercado.  Además de los orígenes de datos de base de datos, SharePoint, OData Service y servicio RIA de WCF, las herramientas de la actualización de marzo de 2014 también ofrecen compatibilidad de primera clase con la puerta de enlace SAP Netweaver.  Cuando se conecta a SAP, la aplicación empresarial de nube ahora admite anotaciones SAP para Phone, WebAddress y Email, simplificando la configuración de las entidades utilizadas desde la puerta de enlace SAP Netweaver.  
  
 **Mejoras en el Asistente para adjuntar origen de datos**  
  
 Muchos orígenes de datos empresariales almacenan un gran número de entidades de datos, pero una aplicación empresarial de nube probablemente necesita interactuar solo con algunos de ellos.  Para facilitar la búsqueda de las entidades con las que desea conectarse, el **Asistente para adjuntar origen de datos** ahora permite buscar las entidades por nombre y filtrar las entidades según categorías diferentes.  También muestra las relaciones de las entidades del origen de datos.  
  
 **Mejoras de rendimiento en la asociación de conjuntos de datos grandes**  
  
 Si la aplicación empresarial de nube necesita asociar un conjunto de datos grande, observará mejoras de rendimiento en el **Asistente para adjuntar origen de datos**.  La distribución del diseñador de entidades se ha mejorado para los conjuntos de datos grandes de modo que pueda examinar fácilmente las relaciones entre las entidades.  Además, ahora permite cambiar el orden de las propiedades de una entidad.  
  
 **Mejoras de tipos de negocio**  
  
 Además de un gran número de entidades, muchos orígenes de datos empresariales traen consigo tipos de negocio sofisticados, como tipos complejos.  La actualización de marzo de 2014 incluye nueva compatibilidad con tipos de datos complejos.  
  
 Si la aplicación empresarial de nube se asocia a una lista de SharePoint que incluye columnas de tipo **Persona**, esas columnas se activan automáticamente como contactos al ejecutar la aplicación.  Por ejemplo, si tiene Lync instalado en el equipo y se conecta a la misma instancia de Active Directory que usa el sitio de SharePoint, la columna de tipo person muestra los valores como contactos de Lync y activa las características de Lync automáticamente en la aplicación empresarial de nube.  
  
### Integrar documentos  
 El almacenamiento y la recuperación de documentos es un requisito común de muchas aplicaciones empresariales.  Por ejemplo, puede que desee proporcionar acceso a una lista de documentos relacionados con un producto cuando el usuario ve los detalles del producto.  También puede ser conveniente permitir a los usuarios administrar los documentos de la aplicación.  Las aplicaciones empresariales de nube ahora permiten la asociación a una biblioteca de documentos de SharePoint y la configuración de una relación entre la entidad de lista y otra entidad de datos.  Con esta funcionalidad, puede compilar rápidamente una aplicación que muestre los documentos relacionados con un campo de datos específico.  
  
 Además, al asociar la aplicación a una biblioteca de documentos web host de SharePoint, las pantallas de la aplicación se integrarán con un conjunto de controles de documentos nuevos, que permiten a los usuarios crear nuevos documentos de Office \(documentos en blanco o a partir de plantillas de documento que están disponibles en la biblioteca de documentos asociada\), abrir documentos en la aplicación web de Office o en el cliente de Office y cargar los documentos existentes.  Todas estas funciones las proporcionan las herramientas, sin requerir ninguna acción adicional por su parte.  
  
### Mejoras en el desarrollo rápido de aplicaciones  
 **Control de resumen mejorado**  
  
 Con el fin de facilitar el trabajo con tipos de datos diferentes, el control de resumen se actualiza para mostrar el control predeterminado para el tipo semántico subyacente.  Con esta compatibilidad, si el control de resumen se asocia a un tipo **Persona**, el control de resumen usará el control **Visor de usuarios**, que muestra información adicional sobre una persona \(por ejemplo, el nombre de la persona, su cargo y su imagen para mostrar\).  
  
> [!NOTE]
>  La propiedad `contentItem.value` para el control de resumen devuelve ahora el valor de la propiedad summary en lugar de la entidad de datos completa.  Si ha utilizado `contentItem.value` para un control de resumen a fin de obtener la entidad para tener acceso a otra propiedad de la entidad, deberá actualizar el código para usar `contentItem.data` en su lugar.  
  
 **Lógica integrada para filtrar conjuntos de datos grandes en las pantallas**  
  
 La actualización de marzo de 2014 incluye compatibilidad integrada para el filtrado de datos.  Sin que sea necesario ninguna acción adicional por su parte, la aplicación empresarial de nube genera pantallas optimizadas para el móvil, que permiten a los usuarios buscar en tablas de datos y ordenar las tablas con encabezados de tabla.  
  
 **Crear conjuntos de pantallas**  
  
 Para ayudarle a compilar rápidamente las pantallas de uso general para que los usuarios examinen, vean y editen datos en la aplicación, en esta versión se ha incluido un conjunto de pantallas común.  En lugar de crear pantallas de navegación, vista, creación y edición una por una, ahora se puede elegir la creación de un conjunto de pantallas común, que generará estos tres tipos de pantallas a la vez.  El conjunto de pantallas común también enlaza las tablas de datos, las relaciones y la navegación entre pantallas automáticamente.  
  
 **Usar marcadores en aplicaciones**  
  
 Los usuarios normalmente desean marcar una página de la aplicación para cambiar rápidamente a esa página.  Las aplicaciones empresariales de nube de esta versión admiten el uso de marcadores sin que sea necesario escribir código.  Permite a los usuarios marcar cualquier página de la aplicación.  También pueden anclar una página en la pantalla de inicio en sus dispositivos móviles.  
  
##  <a name="office"></a> Novedades en el desarrollo de aplicaciones para Office  
 **Nuevos tipos de aplicaciones para Office**  
  
 Office 2013 SP1 y Office 365 admiten aplicaciones de contenido de PowerPoint y aplicaciones de Access Web App, y permiten que la aplicación de correo se active en formularios de redacción \(por ejemplo, cuando los usuarios están escribiendo un nuevo mensaje de correo electrónico o están creando una nueva cita\).  La actualización de marzo de 2014 admite todos estos nuevos tipos de aplicación a lo largo del ciclo de desarrollo completo: creación del proyecto, edición del manifiesto, programación, depuración y publicación.  Napa también se ha actualizado para admitir estos nuevos tipos de aplicación.  
  
 **Plantillas de proyecto actualizadas**  
  
 La aplicación del asistente para la creación de proyectos de Office en Office Developer Tools se ha actualizado para proporcionar opciones más organizadas para la creación de aplicaciones.  Especialmente para las aplicaciones de contenido, en esta versión se incluyen como novedad dos plantillas de proyecto.  Una es simplemente para crear una aplicación básica, que contiene código de ejemplo mínimo, mientras que la otra contiene más código de ejemplo con el fin de mostrar cómo implementar una aplicación para Excel y Access Web App para visualizar los datos.  Puede elegir entre estas dos plantillas de proyecto en el asistente para la creación de proyectos si desea un tutorial para la aplicación.  
  
 **Más opciones para activar la aplicación**  
  
 Más allá de los nuevos tipos de aplicación, Office 2013 SP1 y Office 365 habilitan una nueva manera de especificar el momento en que se puede activar la aplicación.  Además de los hosts de aplicación en los que se puede activar la aplicación \(Word, Excel, PowerPoint, etc.\), definen una lista de conjuntos de API, cada uno de los cuales representa un conjunto de API JSOM de Office con la misma semántica \(Selection, TableBindings, etc.\). Para esas API de Office que se llaman en las funciones principales de la aplicación, se pueden agregar los conjuntos de API correspondientes en el manifiesto de aplicación de modo que la aplicación no se active en los hosts de Office que no admitan esas API.  Al hacer esto, puede tener la aplicación activa en tantos host como sea posible en versiones diferentes, sin agregar lógica de programación compleja.  
  
 Para admitir este tipo de activación, las herramientas de aplicación para Office incluyen como novedad una página Activar en los editores de manifiesto de aplicación del panel de tareas y de contenido.  Permite actualizar conjuntos de API para la aplicación, y también muestra dónde se activará la aplicación en función de los conjuntos de API y hosts de aplicación que se seleccionen.  
  
 **Compatibilidad con IntelliSense mejorada**  
  
 Con el fin de proporcionar una mejor experiencia de programación para los nuevos tipos de aplicación y el nuevo modelo de activación de aplicación, IntelliSense también ha evolucionado.  IntelliSense solo muestra las API válidas para los hosts de la aplicación de destino.  Por ejemplo, si compila una aplicación de contenido destinada solo a Access Web App, las API que se admiten en Access Web App se mostrarán en IntelliSense, pero no otras.  Si compila una aplicación de correo únicamente para formularios de redacción, las API de aplicación de correo de formularios de lectura estarán ocultas para IntelliSense de modo que nunca puedan usarse esas API por error.  Por otra parte, la página Activación del editor de manifiestos de aplicación del panel de tareas y de contenido incluye una opción que puede seleccionar para mostrar solo IntelliSense con las API que pertenecen a los conjuntos de API que especificó en el manifiesto.  
  
 **Mejoras en la depuración**  
  
 La actualización de marzo de 2014 proporciona también más opciones de depuración.  Las aplicaciones del panel de tareas y contenido de Excel se pueden depurar en Office Web App y en el cliente de escritorio.  Puede elegir entre IE, Chrome y Firefox \(si están instalados en el equipo\) en la ventana de propiedades del proyecto de aplicación para iniciar Office Web App para la depuración.  
  
 Además de la compatibilidad con la depuración de Office Web App, las nuevas herramientas también permiten depurar “Solo mi código” para las aplicaciones de Office y SharePoint.  Con esta opción habilitada, no le molestarán más las excepciones de JavaScript que son irrelevantes para el código.  
  
##  <a name="sharepoint"></a> Novedades en el desarrollo de aplicaciones para SharePoint  
 **Versiones diferentes de SharePoint como destino**  
  
 Las herramientas de aplicación para SharePoint no permiten que la aplicación tenga como destino SharePoint Server 2013 \(que es compatible con SharePoint Online\) o solo SharePoint Online.  A través de un modificador simple en la página de propiedades del proyecto de aplicación para SharePoint, las herramientas actualizarán según corresponda el número de versión de SharePoint y las referencias de ensamblado de los componentes de cliente de SharePoint utilizadas en el proyecto.  
  
 **Compatibilidad de MVS con elementos web de cliente**  
  
 Para mejorar la compatibilidad con las aplicaciones web MVC, en esta versión se ha agregado la compatibilidad de MVC con páginas de elementos web de cliente.  Siempre y cuando el proyecto de aplicación para SharePoint esté asociado a una aplicación MVC, al agregar un elemento web de cliente y elegir la creación de una nueva página de elementos en el asistente para creación de elementos web de cliente, se agregarán un controlador de elementos web de cliente y una vista predeterminada para acompañar al controlador de elementos web de cliente en la aplicación MVC en lugar de una página .aspx.  
  
 **Compatibilidad con instancias de lista para receptores de eventos remotos**  
  
 En Visual Studio 2013, el asistente para la creación de receptores de eventos remotos solo permite elegir una plantilla de lista.  Ahora, el asistente también muestra todas las instancias de lista del proyecto para que pueda elegir y crear un receptor de eventos remotos.  Las herramientas crearán el manifiesto correcto en función de lo que seleccione.  
  
 **Generación mejorada de plantillas de lista**  
  
 Esta versión también incluye una corrección para el elemento de plantilla de lista de SharePoint.  Con la actualización de marzo de 2014, cuando se crea una plantilla de lista de SharePoint, el atributo Type del manifiesto de la plantilla de lista se establece en el tipo de la plantilla principal \(en lugar del antiguo valor predeterminado “10000”\).  Con esta corrección, la nueva plantilla de lista hereda todas las propiedades de la plantilla principal de forma gratuita.  Es especialmente útil para los tipos de plantilla de lista sofisticados, como las bibliotecas de documentos, que contienen muchas características personalizadas.