class Resident:
    def __init__(self, name, room_number):
        self.name = name
        self.room_number = room_number

class NursingHomeFrontDesk:
    def __init__(self):
        self.residents = []

    def check_in_resident(self, name, room_number):
        resident = Resident(name, room_number)
        self.residents.append(resident)
        print(f"{resident.name} has been checked in to room {resident.room_number}.")

    def check_out_resident(self, name):
        for resident in self.residents:
            if resident.name == name:
                self.residents.remove(resident)
                print(f"{resident.name} has been checked out.")
                return
        print(f"{name} is not currently checked in.")

    def display_residents(self):
        if not self.residents:
            print("No residents currently checked in.")
        else:
            print("Currently checked-in residents:")
            for resident in self.residents:
                print(f"Name: {resident.name}, Room: {resident.room_number}")


# Example usage
front_desk = NursingHomeFrontDesk()

front_desk.check_in_resident("John Doe", 101)
front_desk.check_in_resident("Jane Smith", 201)
front_desk.check_in_resident("Robert Johnson", 301)

front_desk.display_residents()
# Output:
# Currently checked-in residents:
# Name: John Doe, Room: 101
# Name: Jane Smith, Room: 201
# Name: Robert Johnson, Room: 301

front_desk.check_out_resident("Jane Smith")
front_desk.check_out_resident("Alice Brown")
# Output:
# Jane Smith has been checked out.
# Alice Brown is not currently checked in.

front_desk.display_residents()
# Output:
# Currently checked-in residents:
# Name: John Doe, Room: 101
# Name: Robert Johnson, Room: 301
