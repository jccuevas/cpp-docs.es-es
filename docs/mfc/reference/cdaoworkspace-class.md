---
title: CDaoWorkspace (clase)
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: 6aa404c5eb543db198043dba68d55a4b925739c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253730"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace (clase)

Administra una sesión de base de datos con nombre, protegida mediante contraseña de inicio de sesión a cierre de sesión, por un único usuario.

## <a name="syntax"></a>Sintaxis

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Construye un objeto de área de trabajo. Después, llame a `Create` o `Open`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|Anexa un área de trabajo recién creado a la colección de áreas de trabajo del motor de base de datos.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Inicia una transacción nueva, que se aplica a todas las bases de datos abierto en el área de trabajo.|
|[CDaoWorkspace::Close](#close)|Cierra el área de trabajo y todos los objetos que contiene. Las transacciones pendientes se revierten.|
|[CDaoWorkspace::CommitTrans](#committrans)|Completa la transacción actual y guarda los cambios.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Compacta una base de datos (o duplicados).|
|[CDaoWorkspace::Create](#create)|Crea un nuevo objeto de área de trabajo DAO.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Devuelve el número de objetos de base de datos DAO en la colección de bases de datos del área de trabajo.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Devuelve información acerca de una base de datos DAO especificado definido en la colección de bases de datos del área de trabajo.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Devuelve los valores de inicialización del motor de la ubicación de la base de datos Microsoft Jet en el registro de Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Devuelve un valor que indica si varias transacciones que implican el mismo origen de datos ODBC están aisladas a través de forzar varias conexiones al origen de datos.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Devuelve el número de segundos antes de que se produce un error cuando el usuario intenta iniciar sesión en una base de datos ODBC.|
|[CDaoWorkspace::GetName](#getname)|Devuelve el nombre definido por el usuario para el objeto de área de trabajo.|
|[CDaoWorkspace::GetUserName](#getusername)|Devuelve que el nombre de usuario especificado cuando se creó el área de trabajo. Este es el nombre del propietario del área de trabajo.|
|[CDaoWorkspace::GetVersion](#getversion)|Devuelve una cadena que contiene la versión del motor de base de datos asociado con el área de trabajo.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Devuelve el número de objetos DAO de área de trabajo en la colección de áreas de trabajo del motor de base de datos.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Devuelve información sobre un área de trabajo DAO especificado definido en la colección de áreas de trabajo del motor de base de datos.|
|[CDaoWorkspace::Idle](#idle)|Permite al motor de base de datos realizar tareas en segundo plano.|
|[CDaoWorkspace::IsOpen](#isopen)|Devuelve cero si el área de trabajo abierto.|
|[CDaoWorkspace::Open](#open)|Explícitamente, se abre un objeto de área de trabajo asociado con el área de trabajo de DAO predeterminada.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Intenta reparar una base de datos dañada.|
|[CDaoWorkspace::Rollback](#rollback)|Finaliza la transacción actual y no guardar los cambios.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Establece la contraseña que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin una contraseña específica.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Establece el nombre de usuario que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin un nombre de usuario específico.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Establece los valores de inicialización del motor de la ubicación de la base de datos Microsoft Jet en el registro de Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Especifica si varias transacciones que implican el mismo origen de datos ODBC están aisladas por forzar varias conexiones al origen de datos.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Establece el número de segundos antes de que se produce un error cuando el usuario intenta iniciar sesión en un origen de datos ODBC.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Señala al objeto de área de trabajo subyacente de DAO.|

## <a name="remarks"></a>Comentarios

En la mayoría de los casos, no necesitará varias áreas de trabajo y no necesitará crear objetos de área de trabajo explícito; Cuando se abren los objetos de base de datos y el conjunto de registros, usan el área de trabajo de DAO predeterminada. Sin embargo, si es necesario, puede ejecutar varias sesiones a la vez mediante la creación de objetos adicionales del área de trabajo. Cada objeto de área de trabajo puede contener varios objetos de base de datos abierta en su propia colección de bases de datos. En MFC, un área de trabajo es principalmente un administrador de transacciones, especifican un conjunto de bases de datos abiertas en el mismo "espacio de transacciones."

> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen un prefijo "CDao". En general, las clases MFC basadas en DAO son más eficaces que las clases MFC basadas en ODBC. Las clases basadas en DAO, acceder a datos a través del motor de base de datos Microsoft Jet, incluidos los controladores ODBC. También admiten las operaciones de lenguaje de definición de datos (DDL), como crear bases de datos y agregar tablas y campos mediante las clases, sin tener que llamar a DAO directamente.

## <a name="capabilities"></a>Capacidades

Clase `CDaoWorkspace` proporciona lo siguiente:

- Acceso explícito, si es necesario, para un área de trabajo de forma predeterminada, que se crea al inicializar el motor de base de datos. Normalmente se utiliza el área de trabajo de DAO predeterminada implícitamente mediante la creación de objetos de base de datos y el conjunto de registros.

- Abrir un espacio de transacción en el que las transacciones se aplican a todas las bases de datos del área de trabajo. Puede crear áreas de trabajo adicionales para administrar los espacios de una transacción independiente.

- Una interfaz para muchas de las propiedades del motor de base de datos Microsoft Jet subyacente (consulte las funciones miembro estáticas). Abrir o crear un área de trabajo o una llamada a una función miembro estática antes de abrir o crear, inicializa el motor de base de datos.

- Acceso a la colección de áreas de trabajo del motor de base de datos, que almacena todas las áreas de trabajo activas que se han anexado a él. También puede crear y trabajar con áreas de trabajo sin anexarlos a la colección.

## <a name="security"></a>Seguridad

MFC no implementa las recopilaciones de usuarios y grupos en DAO, que se usan para el control de seguridad. Si necesita esos aspectos de DAO, se debe programar por sí mismo a través de llamadas directas a las interfaces DAO. Para obtener información, consulte [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Uso

Puede usar la clase `CDaoWorkspace` para:

- Abrir explícitamente el área de trabajo predeterminada.

   Normalmente, el uso del área de trabajo predeterminado es implícito, al abrir nuevas [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objetos. Pero es posible que deba obtener acceso a él de forma explícita, por ejemplo, para propiedades del motor de base de datos de acceso o la colección de áreas de trabajo. Consulte "Uso implícito del área de trabajo predeterminado" a continuación.

- Crear nuevas áreas de trabajo. Llame a [Append](#append) si desea agregarlos a la colección de áreas de trabajo.

- Abrir un área de trabajo existente en la colección de áreas de trabajo.

Crear una nueva área de trabajo que aún no existe en las áreas de trabajo se describe en la colección el [crear](#create) función miembro. Los objetos del área de trabajo no se conservan en absoluto entre sesiones del motor de base de datos. Si la aplicación vincule estáticamente a MFC, finaliza la aplicación anula la inicialización del motor de base de datos. Si la aplicación está vinculado dinámicamente a MFC, el motor de base de datos se ha inicializado cuando se descarga la DLL de MFC.

Abriendo el área de trabajo de forma predeterminada, o explícitamente al abrir un área de trabajo existente en la colección de áreas de trabajo, se describe en el [abierto](#open) función miembro.

Finalizar una sesión del área de trabajo al cerrar el área de trabajo con el [cerrar](#close) función miembro. `Close` cierra las bases de datos que no ha cerrado previamente, revirtiendo las transacciones no confirmadas.

## <a name="transactions"></a>Transacciones

DAO administra las transacciones en el nivel de área de trabajo; por lo tanto, las transacciones en un área de trabajo con varias bases de datos abiertos se aplican a todas las bases de datos. Por ejemplo, si dos bases de datos dispone de las actualizaciones no confirmadas y se llama a [CommitTrans](#committrans), se confirman todas las actualizaciones. Si desea limitar las transacciones de una sola base de datos, necesita un objeto de área de trabajo independiente para él.

## <a name="implicit-use-of-the-default-workspace"></a>Uso implícito de área de trabajo predeterminada

MFC utiliza del área de trabajo predeterminada de DAO implícitamente en las siguientes circunstancias:

- Si crea un nuevo `CDaoDatabase` objeto pero no lo hace a través de una existente `CDaoWorkspace` objeto MFC crea automáticamente un objeto de área de trabajo temporal, que corresponde al área de trabajo de DAO predeterminada. Si lo hace para varias bases de datos, todos los objetos de base de datos están asociados con el área de trabajo predeterminada. Puede tener acceso a área de trabajo de la base de datos a través de un `CDaoDatabase` miembro de datos.

- De forma similar, si crea un `CDaoRecordset` objeto sin proporcionar un puntero a un `CDaoDatabase` objeto MFC crea un objeto de base de datos temporal y, por extensión, un objeto de área de trabajo temporal. Puede tener acceso a base de datos de un conjunto de registros e, indirectamente en su área de trabajo a través de un `CDaoRecordset` miembro de datos.

## <a name="other-operations"></a>Otras operaciones

También se proporcionan otras operaciones de base de datos, como la reparación de una base de datos dañada o compactar una base de datos.

Para obtener información sobre cómo llamar a DAO directamente y sobre la seguridad DAO, vea [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="append"></a>  CDaoWorkspace::Append

Llame a esta función miembro después de llamar a [crear](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Comentarios

`Append` anexa un objeto de área de trabajo recién creada a la colección de áreas de trabajo del motor de base de datos. Las áreas de trabajo no se conservan entre sesiones del motor de base de datos; se almacenan solo en la memoria, no en el disco. No es necesario anexar un área de trabajo; Si no lo hace, puede usarlo.

Anexa un área de trabajo permanece en la colección de áreas de trabajo en un activo, el estado abierto, hasta que llame a su [cerrar](#close) función miembro.

Para obtener información relacionada, vea el tema "Método Append" en la Ayuda de DAO.

##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans

Llame a esta función miembro para iniciar una transacción.

```
void BeginTrans();
```

### <a name="remarks"></a>Comentarios

Después de llamar a `BeginTrans`, las actualizaciones que realice a la estructura de datos o base de datos surten efecto cuando se confirma la transacción. Dado que el área de trabajo define un espacio de transacción única, la transacción se aplica a todas las bases de datos abiertas en el área de trabajo. Hay dos maneras para completar la transacción:

- Llame a la [CommitTrans](#committrans) función miembro para confirmar la transacción y guardar los cambios en el origen de datos.

- O llame a la [reversión](#rollback) función miembro para cancelar la transacción.

Cierra el objeto de área de trabajo o un objeto de base de datos mientras está pendiente una transacción revierte todas las transacciones pendientes.

Si tiene que aislar las transacciones en un origen de datos ODBC de los que están en otro origen de datos ODBC, vea el [SetIsolateODBCTrans](#setisolateodbctrans) función miembro.

##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace

Construye un objeto `CDaoWorkspace`.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Comentarios

Después de crear el objeto de C++, tiene dos opciones:

- Llamar al objeto [abrir](#open) función miembro para abrir el área de trabajo predeterminada o para abrir un objeto existente en la colección de áreas de trabajo.

- O llamar al objeto [crear](#create) función miembro para crear un nuevo objeto de área de trabajo DAO. Esto inicia explícitamente una nueva sesión del área de trabajo, que se puede hacer referencia a través de la `CDaoWorkspace` objeto. Después de llamar a `Create`, puede llamar a [Append](#append) si desea agregar el área de trabajo a la colección de áreas de trabajo del motor de base de datos.

Vea la descripción de la clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) para obtener información sobre cuando es necesario crear explícitamente un `CDaoWorkspace` objeto. Por lo general, usa áreas de trabajo que se crean de forma implícita cuando se abre un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto sin especificar un área de trabajo o al abrir un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto sin especificar un objeto de base de datos. Objetos DAO de MFC creados de esta forma usan área de trabajo predeterminada del DAO, que se crea una vez y volver a usar.

Para liberar un área de trabajo y sus objetos contenidos, llame al objeto workspace [cerrar](#close) función miembro.

##  <a name="close"></a>  CDaoWorkspace::Close

Llame a esta función miembro para cerrar el objeto de área de trabajo.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Cerrar un objeto de área de trabajo abierto libera el objeto DAO subyacente y, si el área de trabajo es un miembro de la colección de áreas de trabajo, quita de la colección. Una llamada a `Close` es una buena práctica de programación.

> [!CAUTION]
>  Cierre de un objeto de área de trabajo cierra cualquier base de datos abierta en el área de trabajo. Esto da como resultado cualquier abrir conjuntos de registros en las bases de datos que se cierra también, y cualquier actualización o ediciones pendientes se revierte. Para obtener información relacionada, consulte el [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), y [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) funciones miembro.

Los objetos del área de trabajo no son permanentes; solo existen mientras existan referencias a ellos. Esto significa que cuando finaliza la sesión del motor de base de datos, el área de trabajo y su colección de bases de datos no se conservan. Volver a debe crear para la próxima sesión abriendo el área de trabajo y bases de datos nuevo.

Para obtener información relacionada, vea el tema "Método Close" en la Ayuda de DAO.

##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans

Llame a esta función miembro para confirmar una transacción: guardar un grupo de modificaciones y actualizaciones a una o varias bases de datos del área de trabajo.

```
void CommitTrans();
```

### <a name="remarks"></a>Comentarios

Una transacción se compone de una serie de cambios en los datos de la base de datos o su estructura, empezando por una llamada a [BeginTrans](#begintrans). Cuando se completa la transacción, ya sea la confirma o revierte (cancelar los cambios) con [reversión](#rollback). De forma predeterminada, sin transacciones, las actualizaciones de registros se confirman inmediatamente. Una llamada a `BeginTrans` hace que el compromiso de las actualizaciones se retrasa hasta que llame a `CommitTrans`.

> [!CAUTION]
>  Dentro de un área de trabajo, las transacciones son siempre globales para el área de trabajo y no están limitadas a sólo una base de datos o conjunto de registros. Si se realizan operaciones en más de una base de datos o conjunto de registros dentro de una transacción de área de trabajo, `CommitTrans` confirmaciones todas las actualizaciones pendientes, y `Rollback` restaura todas las operaciones en esas bases de datos y conjuntos de registros.

Al cerrar una base de datos o área de trabajo con las transacciones pendientes, las transacciones todas se revierten.

> [!NOTE]
>  Esto no es un mecanismo de confirmación en dos fases. Si no se puede confirmar una actualización, otros todavía confirmará.

##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase

Llame a esta función miembro que se deben compactar un especificado Microsoft Jet (. Base de datos de Microsoft Access).

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszSrcName*<br/>
El nombre de una existente, cierra la base de datos. Puede ser una ruta de acceso completa y nombre de archivo, como "C:\\\MYDB. MDB". Si el nombre de archivo tiene una extensión, debe especificarlo. Si la red es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, como "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Las barras diagonales dobles son necesarias en las cadenas de ruta de acceso porque "\\" es el carácter de escape de C++.)

*lpszDestName*<br/>
La ruta de acceso completa de la base de datos compactado que va a crear. También puede especificar una ruta de acceso de red como con *lpszSrcName*. No puede usar el *lpszDestName* argumento para especificar el mismo archivo de base de datos que *lpszSrcName*.

*lpszPassword*<br/>
Una contraseña, usar cuando desee compactar una base de datos protegida por contraseña. Tenga en cuenta que si usa la versión de `CompactDatabase` que toma una contraseña, debe proporcionar todos los parámetros. Además, como se trata de un parámetro de connect, requiere un formato especial, como se indica a continuación:; PWD = *lpszPassword*. Por ejemplo:; PWD = "Feliz". (Se requiere el punto y coma inicial).

*lpszLocale*<br/>
Se utiliza para especificar el criterio de ordenación para la creación de una expresión de cadena *lpszDestName*. Si omite este argumento aceptando el valor predeterminado de `dbLangGeneral` (ver abajo), la configuración regional de la nueva base de datos es el mismo que el de la base de datos. Los valores posibles son:

- `dbLangGeneral` Inglés, alemán, francés, portugués, italiano y modernas español

- `dbLangArabic` Árabe

- `dbLangCyrillic` Ruso

- `dbLangCzech` Checo

- `dbLangDutch` Holandés

- `dbLangGreek` Griego

- `dbLangHebrew` Hebreo

- `dbLangHungarian` Húngaro

- `dbLangIcelandic` Islandés

- `dbLangNordic` Idiomas nórdicos (Microsoft Jet database engine sólo versión 1.0)

- `dbLangNorwdan` Noruego y danés

- `dbLangPolish` Polaco

- `dbLangSpanish` Español tradicional

- `dbLangSwedfin` Sueco y finés

- `dbLangTurkish` Turco

*nOptions*<br/>
Indica una o varias opciones para la base de datos de destino, *lpszDestName*. Si se omite este argumento aceptando el valor predeterminado, el *lpszDestName* tendrá el mismo cifrado y la misma versión que *lpszSrcName*. Puede combinar el `dbEncrypt` o `dbDecrypt` opción con una de las opciones de versión mediante el operador OR bit a bit. Los valores posibles, que especifican un formato de base de datos, no es una versión de motor de base de datos, son:

- `dbEncrypt` Cifrar la base de datos mientras se compacta.

- `dbDecrypt` Descifrar la base de datos mientras se compacta.

- `dbVersion10` Crear una base de datos que utiliza la versión 1.0 del motor de base de datos Microsoft Jet mientras compacta.

- `dbVersion11` Crear una base de datos que utiliza la versión 1.1 del motor de base de datos Microsoft Jet mientras compacta.

- `dbVersion20` Crear una base de datos que utiliza la versión 2.0 del motor de base de datos Microsoft Jet mientras compacta.

- `dbVersion30` Crear una base de datos que utiliza la versión 3.0 del motor de base de datos Microsoft Jet mientras compacta.

Puede usar `dbEncrypt` o `dbDecrypt` en el argumento de opciones para especificar si desea cifrar o descifrar la base de datos a medida que se compacta. Si se omite una constante de cifrado o si incluye tanto `dbDecrypt` y `dbEncrypt`, *lpszDestName* tendrá el mismo cifrado que *lpszSrcName*. Puede usar una de las constantes de versión en el argumento de opciones para especificar la versión del formato de datos para la base de datos compactado. Esta constante afecta solo a la versión del formato de datos de *lpszDestName*. Puede especificar solo una constante de versión. Si se omite una constante de versión, *lpszDestName* tendrán la misma versión que *lpszSrcName*. Puede compactar *lpszDestName* sólo a una versión que sea igual o posterior a la de *lpszSrcName*.

> [!CAUTION]
>  Si no se cifra una base de datos, es posible, incluso si decide implementar la seguridad de usuario y contraseña, para leer directamente el archivo de disco binario que constituye la base de datos.

### <a name="remarks"></a>Comentarios

Cambiar datos en una base de datos, el archivo de base de datos puede fragmentarse y usar más espacio en disco del necesario. Periódicamente, se debe compactar la base de datos para desfragmentar el archivo de base de datos. La base de datos compactado es normalmente más pequeño. También puede cambiar el orden de intercalación, el cifrado o la versión del formato de datos mientras se copia y compacta la base de datos.

> [!CAUTION]
>  El `CompactDatabase` función miembro no correctamente convertirá una base de datos de Microsoft Access completa de una versión a otra. Sólo el formato de datos se convierte. Objetos definidos por el acceso de Microsoft, como formularios e informes, no se convierten. Sin embargo, los datos se convierten correctamente.

> [!TIP]
>  También puede usar `CompactDatabase` para copiar un archivo de base de datos.

Para obtener más información acerca de las bases de datos con compactación, vea el tema "Método CompactDatabase" en la Ayuda de DAO.

##  <a name="create"></a>  CDaoWorkspace::Create

Llame a esta función miembro para crear un nuevo objeto de área de trabajo DAO y asociarlo con MFC `CDaoWorkspace` objeto.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Una cadena con hasta 14 caracteres que identifica inequívocamente el nuevo objeto de área de trabajo. Debe proporcionar un nombre. Para obtener información relacionada, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

*lpszUserName*<br/>
El nombre de usuario del propietario del área de trabajo. Para conocer los requisitos, consulte el *lpszDefaultUser* parámetro para el [SetDefaultUser](#setdefaultuser) función miembro. Para obtener información relacionada, vea el tema "Propiedad de nombre de usuario" en la Ayuda de DAO.

*lpszPassword*<br/>
La contraseña para el nuevo objeto de área de trabajo. Una contraseña puede tener hasta 14 caracteres y puede contener cualquier carácter excepto ASCII 0 (null). Las contraseñas distinguen mayúsculas de minúsculas. Para obtener información relacionada, vea el tema "Propiedad de contraseña" en la Ayuda de DAO.

### <a name="remarks"></a>Comentarios

Es el proceso general de creación:

1. Construir un [CDaoWorkspace](#cdaoworkspace) objeto.

1. Llamar al objeto `Create` función miembro para crear el área de trabajo subyacente de DAO. Debe especificar un nombre de área de trabajo.

1. Opcionalmente, llame a [Append](#append) si desea agregar el área de trabajo a la colección de áreas de trabajo del motor de base de datos. Puede trabajar con el área de trabajo sin agregarlo.

Después de la `Create` llamada, el objeto de área de trabajo está en estado abierto, listo para su uso. No llame a `Open` después `Create`. No llame a `Create` si el área de trabajo ya existe en la colección de áreas de trabajo. `Create` Inicializa el motor de base de datos si aún no se ha inicializado ya para la aplicación.

##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount

Llame a esta función miembro para recuperar el número de objetos de base de datos DAO en la colección de bases de datos del área de trabajo, el número de bases de datos abiertas en el área de trabajo.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Valor devuelto

El número de bases de datos abiertas en el área de trabajo.

### <a name="remarks"></a>Comentarios

`GetDatabaseCount` es útil si tiene que recorrer todas las bases de datos definidas en la colección de bases de datos del área de trabajo. Para obtener información acerca de una base de datos en la colección, vea [GetDatabaseInfo](#getdatabaseinfo). Uso habitual consiste en llamar a `GetDatabaseCount` para el número de bases de datos abiertos, a continuación, usar ese número como un índice de bucle llamadas repetidas a `GetDatabaseInfo`.

##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo

Llame a esta función miembro para obtener diversos tipos de información acerca de una base de datos abierto en el área de trabajo.

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del objeto de base de datos de colección de bases de datos del área de trabajo, para la búsqueda por índice.

*dbinfo*<br/>
Una referencia a un [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información acerca de la base de datos para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devolver:

- Nombre AFX_DAO_PRIMARY_INFO (valor predeterminado), puede actualizar, las transacciones

- Signo más de información AFX_DAO_SECONDARY_INFO principal: Versión, criterio de ordenación, tiempo de espera de consulta

- AFX_DAO_ALL_INFO principal y secundaria información más: Conectar

*lpszName*<br/>
El nombre del objeto de base de datos, para la búsqueda por nombre. El nombre es una cadena con hasta 14 caracteres que identifica inequívocamente el nuevo objeto de área de trabajo.

### <a name="remarks"></a>Comentarios

Una versión de la función le permite buscar una base de datos por su índice. La otra versión le permite buscar una base de datos por nombre.

Para obtener una descripción de la información devuelta en *dbinfo*, consulte el [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, obtendrá información de los niveles anteriores también.

##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath

Llame a esta función miembro para obtener la ubicación de la base de datos Microsoft Jet de configuración de inicialización del motor en el registro de Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la ubicación del registro.

### <a name="remarks"></a>Comentarios

Puede usar la ubicación para obtener información sobre la configuración para el motor de base de datos. La información devuelta es realmente el nombre de una subclave del registro.

Para obtener información relacionada, vea los temas "Propiedad IniPath" y "Personalización de Windows del registro configuración de acceso a datos" en la Ayuda de DAO.

##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans

Llame a esta función miembro para obtener el valor actual de la propiedad DAO IsolateODBCTrans del área de trabajo.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aíslan; las transacciones de ODBC en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

En algunas situaciones, es posible que deba tener varias transacciones simultáneas pendientes en la misma base de datos ODBC. Para ello, deberá abrir un área de trabajo independiente para cada transacción. Tenga en cuenta que aunque cada área de trabajo puede tener su propia conexión ODBC a la base de datos, esto reduce el rendimiento del sistema. Como aislamiento de transacción no se requiere normalmente, las conexiones ODBC desde varios objetos de área de trabajo abiertos por el mismo usuario se comparten de forma predeterminada.

Algunos servidores ODBC, como Microsoft SQL Server, no permiten transacciones simultáneas en una sola conexión. Si necesita tener más de una transacción pendiente a la vez en una base de datos, establezca la propiedad IsolateODBCTrans en TRUE en cada área de trabajo en cuanto lo abra. Esto fuerza una conexión ODBC independiente para cada área de trabajo.

Para obtener información relacionada, vea el tema "IsolateODBCTrans Property" en la Ayuda de DAO.

##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout

Llame a esta función miembro para obtener el valor actual de la propiedad LoginTimeout DAO del área de trabajo.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Valor devuelto

El número de segundos antes de que se produce un error al intentar iniciar sesión en una base de datos ODBC.

### <a name="remarks"></a>Comentarios

Este valor representa el número de segundos antes de que se produce un error al intentar iniciar sesión en una base de datos ODBC. El valor de LoginTimeout predeterminado es 20 segundos. Cuando LoginTimeout se establece en 0, se produce ningún tiempo de espera y la comunicación con el origen de datos podría dejar de responder.

Al intentar iniciar sesión en una base de datos ODBC, como Microsoft SQL Server, la conexión puede producir un error como resultado errores de red o porque no se está ejecutando el servidor. En lugar de esperar el valor predeterminado 20 segundos para conectarse, puede especificar cuánto tiempo espera el motor de base de datos antes de que se produce un error. Iniciar sesión en el servidor se produce implícitamente como parte de un número de eventos diferentes, como la ejecución de una consulta en una base de datos del servidor externo.

Para obtener información relacionada, vea el tema "Propiedad LoginTimeout" en la Ayuda de DAO.

##  <a name="getname"></a>  CDaoWorkspace::GetName

Llame a esta función miembro para obtener el nombre definido por el usuario del objeto de área de trabajo DAO subyacente el `CDaoWorkspace` objeto.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre definido por el usuario del objeto de área de trabajo DAO.

### <a name="remarks"></a>Comentarios

El nombre es útil para tener acceso al objeto de área de trabajo DAO en la colección de áreas de trabajo del motor de base de datos por nombre.

Para obtener información relacionada, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

##  <a name="getusername"></a>  CDaoWorkspace::GetUserName

Llame a esta función miembro para obtener el nombre del propietario del área de trabajo.

```
CString GetUserName();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que representa el propietario del objeto de área de trabajo.

### <a name="remarks"></a>Comentarios

Para obtener o establecer los permisos para el propietario del área de trabajo, llamar a DAO directamente para comprobar la configuración de la propiedad permisos; Esto determina qué permisos tiene ese usuario. Para trabajar con los permisos, necesita un sistema. Archivo MDA.

Para obtener información sobre cómo llamar a DAO directamente, vea [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Para obtener información relacionada, vea el tema "Propiedad de nombre de usuario" en la Ayuda de DAO.

##  <a name="getversion"></a>  CDaoWorkspace::GetVersion

Llame a esta función miembro para determinar la versión del motor de base de datos Microsoft Jet de uso.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del motor de base de datos asociado al objeto.

### <a name="remarks"></a>Comentarios

El valor devuelto representa el número de versión en el formato "major.minor"; Por ejemplo, "3.0". El número de versión del producto (por ejemplo, 3.0) está formado por el número de versión (3), un punto y el número de versión (0).

Para obtener información relacionada, vea el tema "Propiedad de versión" en la Ayuda de DAO.

##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount

Llame a esta función miembro para recuperar el número de objetos de área de trabajo DAO en la colección de áreas de trabajo del motor de base de datos.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Valor devuelto

El número de áreas de trabajo abiertos en la colección de áreas de trabajo.

### <a name="remarks"></a>Comentarios

Este recuento no incluye las áreas de trabajo abiertos no se anexa a la colección. `GetWorkspaceCount` es útil si tiene que recorrer todas las áreas de trabajo definidos en la colección de áreas de trabajo. Para obtener información sobre una determinada área de trabajo en la colección, consulte [GetWorkspaceInfo](#getworkspaceinfo). Uso habitual consiste en llamar a `GetWorkspaceCount` para el número de áreas de trabajo abiertos, a continuación, usar ese número como un índice de bucle para llamadas repetidas a `GetWorkspaceInfo`.

##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo

Llame a esta función miembro para obtener diversos tipos de información sobre un área de trabajo está abierto en la sesión.

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del objeto de base de datos en la colección de áreas de trabajo para la búsqueda por índice.

*wkspcinfo*<br/>
Una referencia a un [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el área de trabajo para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devolver:

- Nombre AFX_DAO_PRIMARY_INFO (valor predeterminado)

- Signo más de información AFX_DAO_SECONDARY_INFO principal: Nombre de usuario

- AFX_DAO_ALL_INFO principal y secundaria información más: Aislar ODBCTrans

*lpszName*<br/>
El nombre del objeto de área de trabajo, para la búsqueda por nombre. El nombre es una cadena con hasta 14 caracteres que identifica inequívocamente el nuevo objeto de área de trabajo.

### <a name="remarks"></a>Comentarios

Para obtener una descripción de la información devuelta en *wkspcinfo*, consulte el [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, obtenga información para los niveles anteriores también.

##  <a name="idle"></a>  CDaoWorkspace::Idle

Llame a `Idle` para proporcionar el motor de base de datos con la oportunidad de realizar tareas en segundo plano que pueden no estar actualizadas debido al procesamiento de datos complejos.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parámetros

*nAction*<br/>
Acción que se realizará durante el procesamiento en inactividad. Actualmente es la única acción válida `dbFreeLocks`.

### <a name="remarks"></a>Comentarios

Esto suele ocurrir en los entornos de multitarea multiusuario, en el que no hay suficiente tiempo de procesamiento en segundo plano para mantener todos los registros en un conjunto de registros actual.

> [!NOTE]
>  Una llamada a `Idle` no es necesario con bases de datos creadas con la versión 3.0 del motor de base de datos Microsoft Jet. Use `Idle` solo para las bases de datos creados con versiones anteriores.

Normalmente, se quitan los bloqueos de lectura y los datos en objetos de conjunto de registros de tipo dinámico local se actualiza solo cuando no se produzca ninguna otra acción (incluidos los movimientos del mouse). Si se llama periódicamente a `Idle`, proporcione el motor de base de datos con el tiempo para ponerse al día en las tareas de procesamiento mediante la liberación en segundo plano que no sean necesarios bloqueos de lectura. Especificar el `dbFreeLocks` constante como argumento retrasa el procesamiento hasta que se liberen todos los bloqueos de lectura.

Esta función miembro no es necesario en los entornos de usuario único, a menos que se ejecutan varias instancias de una aplicación. El `Idle` función miembro puede aumentar el rendimiento en un entorno multiusuario porque obliga al motor de base de datos para vaciar los datos en el disco, liberando bloqueos de la memoria. También puede liberar los bloqueos de lectura mediante la realización de las operaciones en parte de una transacción.

Para obtener información relacionada, vea el tema "Método inactivo" en la Ayuda de DAO.

##  <a name="isopen"></a>  CDaoWorkspace::IsOpen

Llame a esta función miembro para determinar si el `CDaoWorkspace` objeto está abierto, es decir, si el objeto MFC se ha inicializado mediante una llamada a [abrir](#open) o una llamada a [crear](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de área de trabajo está abierto; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Se puede llamar a cualquiera de los miembros funciones de un área de trabajo que se encuentra en un estado abierto.

##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace

Un puntero al objeto de área de trabajo subyacente de DAO.

### <a name="remarks"></a>Comentarios

Utilice a este miembro de datos si se necesita acceso directo a objeto DAO subyacente. Puede llamar a las interfaces del objeto DAO a través de este puntero.

Para obtener información sobre el acceso a objetos DAO directamente, vea [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>  CDaoWorkspace::Open

Explícitamente, se abre un objeto de área de trabajo asociado con el área de trabajo de DAO predeterminada.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre del objeto para abrir el área de trabajo DAO, una cadena con hasta 14 caracteres que identifica inequívocamente el área de trabajo. Acepte el valor predeterminado es NULL para abrir explícitamente el área de trabajo predeterminada. Para los requisitos de nomenclatura, consulte el *lpszName* parámetro [crear](#create). Para obtener información relacionada, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

### <a name="remarks"></a>Comentarios

Después de crear un `CDaoWorkspace` de objeto, llame a esta función miembro para que realice una de las siguientes acciones:

- Abrir explícitamente el área de trabajo predeterminada. Pasar NULL como *lpszName*.

- Abra una existente `CDaoWorkspace` (objeto), un miembro de la colección de áreas de trabajo, por su nombre. Pase un nombre válido para un objeto de área de trabajo existente.

`Open` coloca el objeto de área de trabajo en un estado abierto y también inicializa el motor de base de datos si aún no se ha inicializado ya para la aplicación.

Aunque muchos `CDaoWorkspace` miembro funciones solo se pueden llamar después de abrir el área de trabajo, están disponibles las siguientes funciones de miembro, que se ejecuta en el motor de base de datos, después de la construcción del objeto de C++, pero antes de llamar a `Open`:

||||
|-|-|-|
|[Crear](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Idle](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase

Llame a esta función miembro si tiene que intentar reparar una base de datos dañada que obtiene acceso al motor de base de datos Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
La ruta de acceso y nombre de un archivo de base de datos de motor de Microsoft Jet existente. Si se omite la ruta de acceso, se busca sólo el directorio actual. Si su sistema es compatible con la convención de nomenclatura uniforme (UNC), también puede especificar una ruta de acceso de red, como: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Las barras diagonales dobles son necesarias en la cadena de ruta de acceso porque "\\" es el carácter de escape de C++.)

### <a name="remarks"></a>Comentarios

Debe cerrar la base de datos especificado por *lpszName* antes de repararla. En un entorno multiusuario, otros usuarios no pueden tener *lpszName* abrir mientras que va a reparar. Si *lpszName* no está cerrada o no está disponible para su uso exclusivo, se produce un error.

Esta función miembro intenta reparar una base de datos que se marcó como dañada por una operación de escritura incompleta. Esto puede ocurrir si una aplicación mediante el motor de base de datos Microsoft Jet se cierra inesperadamente debido a un problema de hardware de interrupción o el equipo de energía. Si completa la operación y llame a la [cerrar](../../mfc/reference/cdaodatabase-class.md#close) función miembro o salga de la aplicación de una forma habitual, la base de datos, no se marcará como posiblemente dañado.

> [!NOTE]
>  Después de reparar una base de datos, también es una buena idea para compactar mediante el [CompactDatabase](#compactdatabase) función de miembro para desfragmentar el archivo y para recuperar espacio en disco.

Para obtener más información acerca de cómo reparar bases de datos, vea el tema "Método RepairDatabase" en la Ayuda de DAO.

##  <a name="rollback"></a>  CDaoWorkspace::Rollback

Llame a esta función miembro para finalizar la transacción actual y restaurar todas las bases de datos del área de trabajo a su condición antes de que se ha confirmado la transacción.

```
void Rollback();
```

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Dentro de un objeto de área de trabajo, las transacciones son siempre globales para el área de trabajo y no están limitadas a sólo una base de datos o conjunto de registros. Si se realizan operaciones en más de una base de datos o conjunto de registros dentro de una transacción de área de trabajo, `Rollback` restaura todas las operaciones en todas las bases de datos y conjuntos de registros.

Si cierra un objeto de área de trabajo sin guardar o revertir las transacciones pendientes, las transacciones se revierten automáticamente. Si se llama a [CommitTrans](#committrans) o `Rollback` sin llamar primero a [BeginTrans](#begintrans), se produce un error.

> [!NOTE]
>  Al iniciar una transacción, el motor de base de datos registra sus operaciones en un archivo que se guarda en el directorio especificado por la variable de entorno TEMP en la estación de trabajo. Si el archivo de registro de transacciones agota el almacenamiento disponible en la unidad TEMP, el motor de base de datos hará que MFC producir un `CDaoException` (error DAO, 2004). En este punto, si se llama a `CommitTrans`, un número indeterminado de operaciones se confirman, pero se pierden las operaciones restantes no completadas y la operación tiene que reiniciarse. Una llamada a `Rollback` libera el registro de transacciones y deshace todas las operaciones en la transacción.

##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword

Llame a esta función miembro para establecer la contraseña predeterminada que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin una contraseña específica.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszPassword*<br/>
La contraseña predeterminada. Una contraseña puede tener hasta 14 caracteres y puede contener cualquier carácter excepto ASCII 0 (null). Las contraseñas distinguen mayúsculas de minúsculas.

### <a name="remarks"></a>Comentarios

La contraseña predeterminada que establece se aplica a nuevas áreas de trabajo que se creen después de la llamada. Al crear áreas de trabajo subsiguientes, no es necesario especificar una contraseña en el [crear](#create) llamar.

Para usar esta función miembro:

1. Construir un `CDaoWorkspace` objeto pero no llame a `Create`.

1. Llame a `SetDefaultPassword` y, si lo desea, [SetDefaultUser](#setdefaultuser).

1. Llame a `Create` para este objeto de área de trabajo o las posteriores, sin especificar una contraseña.

De forma predeterminada, la propiedad DefaultUser está establecida en "admin" y la propiedad DefaultPassword está establecida en una cadena vacía ("").

Para obtener más información acerca de la seguridad, vea el tema "Permisos de propiedad" en la Ayuda de DAO. Para obtener información relacionada, vea los temas "Propiedad DefaultPassword" y "DefaultUser Property" en la Ayuda de DAO.

##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser

Llame a esta función miembro para establecer el nombre de usuario predeterminado que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin un nombre de usuario específico.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parámetros

*lpszDefaultUser*<br/>
El nombre de usuario predeterminado. Un nombre de usuario puede tener una longitud de 1 a 20 caracteres e incluir caracteres alfabéticos, caracteres acentuados, números, espacios y los símbolos, excepto para: "(comillas), / (barra diagonal), \ (barra diagonal inversa), \[ \] (corchetes),: (dos puntos), &#124; () barra vertical), \< (menor-que el inicio de sesión), > (mayor-que el inicio de sesión), + (signo más), = (signo igual), (punto y coma), (coma), (signo de interrogación), \* (asterisco), espacios y caracteres de control (ASCII 00 y 31 ASCII) líderes. Para obtener información relacionada, vea el tema "Propiedad de nombre de usuario" en la Ayuda de DAO.

### <a name="remarks"></a>Comentarios

El nombre de usuario predeterminado que establece se aplica a nuevas áreas de trabajo que se creen después de la llamada. Al crear áreas de trabajo subsiguientes, no es necesario especificar un nombre de usuario en el [crear](#create) llamar.

Para usar esta función miembro:

1. Construir un `CDaoWorkspace` objeto pero no llame a `Create`.

1. Llame a `SetDefaultUser` y, si lo desea, [SetDefaultPassword](#setdefaultpassword).

1. Llame a `Create` para este objeto de área de trabajo o las posteriores, sin especificar un nombre de usuario.

De forma predeterminada, la propiedad DefaultUser está establecida en "admin" y la propiedad DefaultPassword está establecida en una cadena vacía ("").

Para obtener información relacionada, vea los temas "Propiedad DefaultUser" y "DefaultPassword Property" en la Ayuda de DAO.

##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath

Llame a esta función miembro para especificar la ubicación de la configuración del registro de Windows para el motor de base de datos Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parámetros

*lpszRegistrySubkey*<br/>
Una cadena que contiene el nombre de una subclave del registro de Windows para la ubicación de configuración del motor de base de datos Microsoft Jet o los parámetros necesarios para las bases de datos ISAM instalables.

### <a name="remarks"></a>Comentarios

Llamar a `SetIniPath` solo si tiene que especificar una configuración especial. Para obtener más información, vea el tema "Propiedad IniPath" en la Ayuda de DAO.

> [!NOTE]
>  Llamar a `SetIniPath` durante la instalación de la aplicación, no cuando se ejecuta la aplicación. `SetIniPath` debe llamarse antes de abrir cualquier áreas de trabajo, las bases de datos o conjuntos de registros; en caso contrario, MFC inicia una excepción.

Puede usar este mecanismo para configurar el motor de base de datos con la configuración del registro proporcionado por el usuario. El ámbito de este atributo se limita a la aplicación y no se puede cambiar sin tener que reiniciar la aplicación.

##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans

Llame a esta función miembro para establecer el valor de la propiedad IsolateODBCTrans DAO para el área de trabajo.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parámetros

*bIsolateODBCTrans*<br/>
Pasar TRUE si desea empezar a aislar las transacciones de ODBC. Pase el valor FALSE si desea detener el aislamiento de transacciones de ODBC.

### <a name="remarks"></a>Comentarios

En algunas situaciones, es posible que deba tener varias transacciones simultáneas pendientes en la misma base de datos ODBC. Para ello, deberá abrir un área de trabajo independiente para cada transacción. Aunque cada área de trabajo puede tener su propia conexión ODBC a la base de datos, esto reduce el rendimiento del sistema. Como aislamiento de transacción no se requiere normalmente, las conexiones ODBC desde varios objetos de área de trabajo abiertos por el mismo usuario se comparten de forma predeterminada.

Algunos servidores ODBC, como Microsoft SQL Server, no permiten transacciones simultáneas en una sola conexión. Si necesita tener más de una transacción pendiente a la vez en una base de datos, establezca la propiedad IsolateODBCTrans en TRUE en cada área de trabajo en cuanto lo abra. Esto fuerza una conexión ODBC independiente para cada área de trabajo.

##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout

Llame a esta función miembro para establecer el valor de la propiedad LoginTimeout DAO para el área de trabajo.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parámetros

*nSeconds*<br/>
El número de segundos antes de que se produce un error al intentar iniciar sesión en una base de datos ODBC.

### <a name="remarks"></a>Comentarios

Este valor representa el número de segundos antes de que se produce un error al intentar iniciar sesión en una base de datos ODBC. El valor de LoginTimeout predeterminado es 20 segundos. Cuando LoginTimeout se establece en 0, se produce ningún tiempo de espera y la comunicación con el origen de datos podría dejar de responder.

Al intentar iniciar sesión en una base de datos ODBC, como Microsoft SQL Server, la conexión puede producir un error como resultado errores de red o porque no se está ejecutando el servidor. En lugar de esperar el valor predeterminado 20 segundos para conectarse, puede especificar cuánto tiempo espera el motor de base de datos antes de que se produce un error. Iniciar sesión en el servidor se produce implícitamente como parte de un número de eventos diferentes, como la ejecución de una consulta en una base de datos del servidor externo. El valor de tiempo de espera viene determinada por la configuración actual de la propiedad LoginTimeout.

Para obtener información relacionada, vea el tema "Propiedad LoginTimeout" en la Ayuda de DAO.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
