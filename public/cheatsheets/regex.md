# List of Handy Regular Expressions

#### Username (Remove A-Z if case sensitive, change {3,16} for desired length limits)
`/^[a-zA-Z0-9_-]{3,16}$/`

#### Password (Change {6,18} for desired length limits)
`/^[a-z0-9_-]{6,18}$/`

#### Hex
`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

#### Slug
`/^[a-z0-9-]+$/`

#### Email
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

#### URL
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

#### IP address
`/^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/`

#### HTML Tag
`/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

#### Match any non-ASCII character
`/[^\x00-\x7F]+/`

#### Match any non-Unicode character
`[^\u0000-\u007F]+`
