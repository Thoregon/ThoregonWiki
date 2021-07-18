UI
==


conditional references to UI elements
select which view should be displayed depending on a condtion
can be used in <aurora-view> and <aurora-link>

a condition is expressed by a '@' at start
this properties can be used in the condition
- view attributes
- viewmodel properties
- model properties
- component interface properties
- extra properties:
    - loggedin   
 
express a conditon:

if-then: '@property:pathtoview'
    if the property is not null or undefined, the 'pathtoview' is used, otherwise nothing is displayed (view remains empty)

if-then: '@property=xyz:pathtoview'
    if the property has the value 'xyz', the 'pathtoview' is used, otherwise nothing is displayed (view remains empty)

if-then-else: '@property:pathtoview|pathtoanotherview'
    if the property is not null or undefined, the 'pathtoview' is used, otherwise 'pathtoanotherview'

if the else is omittes, another condition can be added with a ','
if-then,if-then-else:   '@property:pathtoview,@property2:pathtoview2|pathtoanotherview2'

 
    <aurora-view view="@loggedin:commentmessagebox|commentmessagebox/login"></aurora-view>

    <aurora-link to="mainpage" view="@loggedin:settings"><span>Settings</span></aurora-link>
