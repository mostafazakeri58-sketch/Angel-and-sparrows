Table donors {
  donor_id integer [pk, increment]
  first_name varchar
  last_name varchar
  email varchar
  phone varchar
  address varchar
  city varchar
  state varchar
}

Table donations {
  donation_id integer [pk, increment]
  donor_id integer
  amount numeric
  date date
}

Ref: donations.donor_id > donors.donor_id

Table staff {
  staff_id integer [pk, increment]
  first_name varchar
  last_name varchar
  role varchar
  department varchar
  email varchar
  phone varchar
}

Table volunteers {
  volunteer_id integer [pk, increment]
  first_name varchar
  last_name varchar
  phone varchar
  email varchar
  availability varchar
  supervisor_staff_id integer
}

Ref: volunteers.supervisor_staff_id > staff.staff_id

Table skills {
  skill_id integer [pk, increment]
  skill_name varchar
}

Table volunteer_skills {
  volunteer_skill_id integer [pk, increment]
  volunteer_id integer
  skill_id integer
  level varchar
}

Ref: volunteer_skills.volunteer_id > volunteers.volunteer_id
Ref: volunteer_skills.skill_id > skills.skill_id

Table volunteer_assignments {
  assignment_id integer [pk, increment]
  volunteer_id integer
  role varchar
  start_time timestamp
  end_time timestamp
}

Ref: volunteer_assignments.volunteer_id > volunteers.volunteer_id

Table events {
  event_id integer [pk, increment]
  name varchar
  date date
  location varchar
}

Table event_participants {
  participant_id integer [pk, increment]
  event_id integer
  donor_id integer
  volunteer_id integer
  staff_id integer
  role varchar
  status varchar
}

Ref: event_participants.event_id > events.event_id
Ref: event_participants.donor_id > donors.donor_id
Ref: event_participants.volunteer_id > volunteers.volunteer_id
Ref: event_participants.staff_id > staff.staff_id
