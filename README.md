# Passage a React

Creer un nouveau projet a l'aide de [CRA](https://fr.reactjs.org/docs/create-a-new-react-app.html#create-react-app)

```
npx create-react-app mon-app
```

## Exploiter les donnees repetitives

Donnees utilisees pour l'exemple :

```
  <select>
    <option value="">Choisir un réseau</option>
    <option value="Facebook">Facebook</option>
    <option value="Twitter">Twitter</option>
    <option value="Instagram">Instagram</option>
    <option value="Linkedin">Linkedin</option>
    <option value="WhatsApp">WhatsApp</option>
    <option value="Snapchat">Snapchat</option>
    <option value="Messenger">Messenger</option>
    <option value="Pinterest">Pinterest</option>
    <option value="TikTok">TikTok</option>
    <option value="Discord">Discord</option>
  </select>
```

Stocker les donnees dans des tableaux d'objet sous une forme facilement exploitable.<br />
**A faire en dehors du composant si aucune donnes n'est dynamique ni dependante du composant ou de ses props**

```
const selectReseauBox = [
  {value: "Facebook", label: "Facebook"},
  {value: "Twitter", label: "Twitter"},
  {value: "Instagram", label: "Instagram"},
  {value: "Linkedin", label: "Linkedin"},
  {value: "WhatsApp", label: "WhatsApp"},
  {value: "Snapchat", label: "Snapchat"},
  {value: "Messenger", label: "Messenger"},
  {value: "Pinterest", label: "Pinterest"},
  {value: "TikTok", label: "TikTok"},
  {value: "Discord", label: "Discord"},
  ]
```

Afficher les donnees en mappant sur le tableau

```
  <select>
    <option value="">Choisir un réseau</option>
    {selectReseauBox.map(reseauBoxOption => <option value={reseauBoxOption.value}>{reseauBoxOption.label}</option>)}
  </select>
```

Utiliser les hooks pour controler le state

```
const [selectedReseauBoxOption, setSelectedReseauBoxOption] = useState("")
```

```
  <select onChange={event => setSelectedReseauBoxOption(event.target.value)}>
    <option value="">Choisir un réseau</option>
    {selectReseauBox.map(reseauBoxOption => <option value={reseauBoxOption.value}>{reseauBoxOption.label}</option>)}
  </select>
```

Je te conseille fortement d'utiliser [Mui](https://mui.com/getting-started/usage/)
Voici l'exemple du dessus en utilisant le composant [Textfield](https://mui.com/components/text-fields/) de cette lib.

```
  <TextField
    select
    label="Choisir un réseau"
    value={selectedReseauBoxOption}
    onChange={event => setSelectedReseauBoxOption(event.target.value)}
  >
    {selectReseauBox.map((option) => (
      <MenuItem key={option.value} value={option.value}>
        {option.label}
      </MenuItem>
    ))}
  </TextField>
```

Il ne reste qu'a reproduire l'exemple pour que ca reponde a ton besoin sur toute la page 💪
