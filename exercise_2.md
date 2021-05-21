1. Design kitties pallet
2. Requirements:
    - Kitty must have a 128 bit DNA, which is randomly generated
    - Kitty must have one owner
    - A user can have zero or more kitties
    - Users can create kitties

1) Following the above sepcification the design would be shown below:

    Types:
      struct Kitty{
        id: string// id can be incremented number assigned to each kitty
        dna: string, //the dna can be generated using the UUID crate available in the rust 
        owner: Owner //Owner of the kitty represented by the struct below
      }

      struct Owner{
          id: string, //unique incremental number assigned to each owner
          name: string //onwer's name
      }

    Calls:
         fn create_kitty(name,gender); // function used to create the kitty by passing the name and gender
         fn transfer_kitty(kitty_id,to, from); //function to transfer the kitty from address to address
         fn sell_kitty(id,amount); // putting the kitty for sale by passing the id and the amount
         fn breed_kitty(); // breeding kitty
         fn unlist_kitty(id); //unlisting the kitty that has been put in sale
         fn buy_kitty(id); //buying the kitty

    Storages:
        kitties: map kitty_id => Kitty
        kitties_for_sale: map kitty_id => amount

    Events
        KittyCreated
            id
            owner
        KittyTransfered
            kitty_id
            to,
            from
        KittySold
            kitty_id
            to
            from
                        